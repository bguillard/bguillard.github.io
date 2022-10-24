---
layout: project
title: "MeshUDF"
permalink: /meshudf/
description: MeshUDF Fast and Differentiable Meshing of Unsigned Distance Field Networks

---
<!-- Import 3D viewer component -->
<script type="module" src="https://unpkg.com/@google/model-viewer/dist/model-viewer.min.js"></script>

<h1 style="text-align: center;">MeshUDF: Fast and Differentiable Meshing of Unsigned Distance Field Networks</h1>

<h2 style="text-align: center;">
    <a class="page-link" href="https://bguillard.github.io/">Benoit Guillard</a>,
    <a class="page-link" href="https://scholar.google.com/citations?user=UxEI4sQAAAAJ&hl=en">Federico Stella</a>,
    <a class="page-link" href="https://people.epfl.ch/pascal.fua?lang=en">Pascal Fua</a>
</h2>


<div class="centered_div big">
    <div class="div_sidebyside"><img src="/projects/meshudf/images/epfl_logo.png"></div>
    <div class="div_sidebyside">
    	<a class="page-link" href="https://www.epfl.ch/labs/cvlab/">
    		<img src="/projects/meshudf/images/cvlab_logo.png"></a></div>
</div>

<div class="centered_div big" style="padding-bottom:20px;">
    <div class="div_rounded_corners"><a href="https://arxiv.org/abs/2111.14549" style="color: #fdfdfd;">
        <i class="ai ai-arxiv"></i> Paper
    </a></div>
    <div class="div_rounded_corners"><p style="color: #fdfdfd;"><object data="/assets/github_logo.svg"></object>
        <a href="https://github.com/cvlab-epfl/MeshUDF" style="color: #fdfdfd;">Code</a>
    </p></div>
</div>

<div class="centered_div big auto-resizable-iframe">
  <div>
    <iframe frameborder="0" allowfullscreen="" src="https://www.youtube.com/embed/TVMwnazd9lQ"></iframe>
  </div>
</div>


<div class="div_abstract">
	<h1 style="text-align: center;">Abstract</h1>
	Unsigned Distance Fields (UDFs) can be used to represent non-watertight surfaces. However, current approaches to converting them into explicit meshes tend to either be expensive or to degrade the accuracy. Here, we extend the marching cube algorithm to handle UDFs, both fast and accurately. Moreover, our approach to surface extraction is differentiable, which is key to using pretrained UDF networks to fit sparse data.
</div>


<hr class="hr_style">

<div class="div_text div_gray">
  <h3> Example </h3>

<table >
<tr>
<td>
	<div class="auto-resizable-mv">
  	<div>
  		<model-viewer interpolation-decay="0" alt="Inflated" src="/projects/meshudf/meshes/pants_inflated2.glb" shadow-intensity="1" poster="/projects/meshudf/meshes/pants_inflated2.png"  orientation="0deg -30deg 0deg" field-of-view="39deg" camera-controls touch-action="pan-y"></model-viewer>
  	</div></div>
</td>
<td>
	<div class="auto-resizable-mv">
  	<div>
  		<model-viewer alt="BP" src="/projects/meshudf/meshes/pants_bp2.glb" shadow-intensity="1" poster="/projects/meshudf/meshes/pants_bp2.png"  orientation="0deg -30deg 0deg" field-of-view="39deg" camera-controls touch-action="pan-y"></model-viewer></div></div>
</td>
<td>
	<div class="auto-resizable-mv">
  	<div>
	<model-viewer interpolation-decay="0" alt="Ours" src="/projects/meshudf/meshes/pants_ours2.glb" poster="/projects/meshudf/meshes/pants_ours2.png" shadow-intensity="1"  orientation="0deg -30deg 0deg" field-of-view="39deg" camera-controls touch-action="pan-y"></model-viewer>
	</div></div>
</td>
</tr>
<tr>

<td><center><small><b>(a)</b><i> [<i>MC</i>] on an ε>0 level set </i></small></center></td>
<td><center><small><b>(b)</b><i> Meshing a point cloud </i></small></center></td>
<td><center><small><b>(c)</b><i> Our procedure </i></small></center></td>
</tr>
</table>


  <div style="width: 100%; display:inline-block;">
    
The UDF of a pair of trousers is meshed by either <b>(a)</b> Marching Cubes [<i>MC</i>] an the ε>0 level set, <b>(b)</b> meshing a dense point cloud as in [<i>NDF</i>], or <b>(c)</b>  our algorithm.
<br>
Using <b>(a)</b>, the shape is inflated and artificially thickened (visible at the leg openings). With <b>(b)</b>, the mesh is open but rough, and the procedure is slow. In contrast, our method <b>(c)</b> quickly obtains an open and regular mesh.

  </div>
</div>


<div class="div_text div_gray">
	<h3> Approach </h3>
  <div class="div_aligned">
    <div class="split_img_if_possible right" ><img style="margin:5px; width:100%;border-radius:10px;" src="/projects/meshudf/images/method.png" /> 
    </div>
    <div class="split_text_if_possible" >
      UDFs do not have sign flips, thus Marching Cubes [<i>MC</i>] does not apply directly. Instead, at each grid cell we rely on gradient orientations to infer local pseudo-signs. To ensure consistency between the pseudo-signs of neighboring grid cells, we explore the grid in a breadth-first manner.
    </div>
  </div>
</div>




<div class="div_text div_gray">
  <h3> Differentiability </h3>
  <div class="div_aligned">
  <div class="split_text_if_possible" >
    When the UDF <i>φ(.)</i> is decoded by a network from a latent code <b>z</b>, we provide gradients for mesh vertices <b>v</b> w.r.t. <b>z</b>.
    Since <b>v</b> lies at a singularity of the field, we control the <b>α>0</b> level sets using differentiability results from [<i>MS</i>]. Intuitively, when the UDF increases at <b>v<sub>-</sub></b> and decreases at <b>v<sub>+</sub></b>, <b>v</b> moves in the direction of the normal <b>n</b>.
  </div>
  <div class="split_img_if_possible left"><img style="margin:5px; border-radius:10px;" src="/projects/meshudf/images/gradients.png" /></div>
  </div>
</div>

<div class="div_text div_gray">
  <h3> Optimization </h3>
    With the above gradients, a frozen UDF decoder can be used as a differentiable parameterization of open surface meshes. In this example, we start from the latent code of a pair of trousers, and optimize it so that the corresponding output mesh matches the silhouette of a tshirt. 
    <br>Using our gradients and a differentiable rasterizer of meshes, we simply minimize a pixel space loss via gradient descent. The latent space traversal eventually results in a topology change.
    <div style="width: 100%; display:block; margin:auto; padding-bottom:2px;"><img style="margin:5px; border-radius:10px;" src="/projects/meshudf/images/silh_optim.gif" /></div>
  	<div style="width: 100%; display:inline-block;">
  </div>
</div>

<h2> BibTeX </h2>
If you find our work useful, please cite it:

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>@inproceedings{guillard2022udf,
  author = {Guillard, Benoit and Stella, Federico and Fua, Pascal},
  title = {MeshUDF: Fast and Differentiable Meshing of Unsigned Distance Field Networks},
  booktitle = {European Conference on Computer Vision},
  year = {2022}
}
</code></pre></div></div>


<hr class="hr_style_thin">

<h3> References </h3>


<div class="div_refs">
  <div class="div_aligned_top">
    <div style="width: 12%; display:inline-block; text-align:right; margin-right:1%;">[<i>MC</i>]</div>
    <div style="width: 87%; display:inline-block;">Marching Cubes: a High Resolution 3D Surface Construction Algorithm, Lorensen and Cline, <i>SIGGRAPH</i> 1987.</div>
  </div>
</div>
<div class="div_refs">
  <div class="div_aligned_top">
    <div style="width: 12%; display:inline-block; text-align:right; margin-right:1%;">[<i>NDF</i>]</div>
    <div style="width: 87%; display:inline-block;">Neural Unsigned Distance Fields for Implicit Function Learning, Chibane et al., <i>NeurIPS</i> 2020.</div>
  </div>
</div>
<div class="div_refs">
  <div class="div_aligned_top">
    <div style="width: 12%; display:inline-block; text-align:right; margin-right:1%;">[<i>MS</i>]</div>
    <div style="width: 87%; display:inline-block;">MeshSDF: Differentiable Iso-Surface Extraction, Remelli et al., <i>NeurIPS</i> 2020.</div>
  </div>
</div>