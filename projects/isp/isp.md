---
layout: project
title: "ISP"
permalink: /isp/
description: ISP Multi-Layered Garment Draping with Implicit Sewing Patterns

---
<!-- Import 3D viewer component -->
<script type="module" src="https://unpkg.com/@google/model-viewer/dist/model-viewer.min.js"></script>

<h1 style="text-align: center;">ISP: Multi-Layered Garment Draping with Implicit Sewing Patterns</h1>

<h2 style="text-align: center;">
    <a class="page-link" href="https://liren2515.github.io/page/">Ren Li</a>,
    <a class="page-link" href="https://bguillard.github.io/">Benoit Guillard</a>,
    <a class="page-link" href="https://people.epfl.ch/pascal.fua?lang=en">Pascal Fua</a>
</h2>


<div class="centered_div big">
    <div class="div_sidebyside"><img src="/projects/meshudf/images/epfl_logo.png"></div>
    <div class="div_sidebyside">
    	<a class="page-link" href="https://www.epfl.ch/labs/cvlab/">
    		<img src="/projects/meshudf/images/cvlab_logo.png"></a></div>
</div>

<div class="centered_div big" style="padding-bottom:20px;">
    <div class="div_rounded_corners"><a href="https://arxiv.org/abs/2305.14100" style="color: #fdfdfd;">
        <i class="ai ai-arxiv"></i> Paper
    </a></div>
    <div class="div_rounded_corners"><p style="color: #fdfdfd;"><object data="/assets/github_logo.svg"></object>
        <a href="https://github.com/liren2515/ISP" style="color: #fdfdfd;">Code</a>
    </p></div>
</div>

<div class="centered_div big auto-resizable-iframe">
  <div>
    <iframe frameborder="0" allowfullscreen="" src="https://www.youtube.com/embed/f2t8XglQOuM"></iframe>
  </div>
</div>


<div class="div_abstract">
	<h1 style="text-align: center;">Abstract</h1>
  We introduce a learned parametric garment representation model that can handle <u>multi-layered clothing</u>. As in models used by clothing designers, each garment consists of individual 2D panels. Their 2D shape is defined by a Signed Distance Function, and 3D shape by a 2D to 3D mapping. 
  We show that this combination is faster and yields higher quality reconstructions than purely implicit surface representations. It makes the recovery of layered garments from images possible thanks to its differentiability, and the 2D parameterization enables easy detection of potential collisions. Furthermore, it supports rapid editing of garment shapes and texture by modifying individual 2D panels.
</div>


<hr class="hr_style">

<div class="div_text div_gray">
  <h3> Example </h3>

<table >
<tr >
<td>
	<div class="auto-resizable-mv" >
  	<div style="padding-bottom: 100%;">
  		<model-viewer camera-orbit="0deg 0deg 1m" alt="MeshUDF" src="/projects/isp/meshes/udf.glb" shadow-intensity="1" poster="/projects/isp/meshes/udf.png"  orientation="0deg -30deg 0deg" camera-controls touch-action="pan-y"></model-viewer></div></div>
</td>
<td>
	<div class="auto-resizable-mv" >
  	<div style="padding-bottom: 100%;">
  		<model-viewer camera-orbit="0deg 0deg 1m" interpolation-decay="0" alt="ISP" src="/projects/isp/meshes/isp.glb" shadow-intensity="1" poster="/projects/isp/meshes/isp.png"  orientation="0deg -30deg 0deg"  camera-controls touch-action="pan-y"></model-viewer>
  	</div></div>
</td>
</tr>
<tr>

<td><center><small><b>(a)</b><i> MeshUDF [<i>MU</i>], in ~2300ms </i></small></center></td>
<td><center><small><b>(b)</b><i> Our method, in ~80ms </i></small></center></td>
</tr>
</table>


  <div style="width: 100%; display:inline-block;">

  An open vest is reconstructed with either <b>(a)</b> an implicit surface representation (MeshUDF, [<i>MU</i>]), or <b>(b)</b> our method.

  Using <b>(a)</b>, the shape has wavy and irregular <u>borders</u>, and the procedure is slow. In contrast, our method <b>(b)</b> quickly obtains a more regular mesh.

  </div>
</div>


<div class="div_text div_gray">
	<h3> Approach </h3>
  <div class="div_aligned">
    <div class="split_img_if_possible right" ><img style="margin:5px; width:100%;border-radius:10px;" src="/projects/isp/images/patterns.png" /> 
    </div>
    <div class="split_text_if_possible" style="width: 100%;" >
      We represent 3D digital garments as flat sewing patterns that are deformed and stitched together. For example, this shirt is naturally decomposed into a front and a back panel, shown in grey and purple. When flattened, each panel has a distinct shape, and the numbers indicate which edges align and need to be stitched together.
    </div>
  </div>
  To learn a latent space of such representations, we use two neural networks. The first one parametrizes the sewing patterns as 2D SDFs with labels for the edges. The second one lifts the flat panels to 3D with a continuous uv deformation, in the manner of AtlasNet [AN]. This results in one 3D mesh for each panel, which are then stitched together.
  <div style="width: 100%; display:block; margin:auto; padding-bottom:2px;"><img style="margin:5px; border-radius:10px;" src="/projects/isp/images/networks.png" /></div>
</div>


<div class="div_text div_gray">
	<h3> Draping </h3> 
  In order to fit garments onto different body poses and shapes, we adopt techniques from both <a href="https://liren2515.github.io/page/drapenet/drapenet.html">DrapeNet</a> and <a href="http://mslab.es/projects/SNUG/">SNUG</a>. We train a deformation network using a self-supervised approach. What sets our method apart is a new parameterization that allows us to extend the draping process across multiple layers. We base our reasoning on the UV-maps of each panel to easily detect intersections. When found, these intersections can be corrected using another neural network, specifically a 2D CNN. This results in an iterative process where garments are draped sequentially according to their natural order.
  <div style="width: 100%; display:block; margin:auto; padding-bottom:2px;"><img style="margin:5px; border-radius:10px;" src="/projects/isp/images/drapings.jpg" /></div>
</div>


<div class="div_text div_gray">
  <h3> Garment Modifications </h3>
  <div class="div_aligned">
  <div class="split_text_if_possible" >
    By working within the UV space of our garment parameterization, we can easily make modifications. For instance, sketching on a single pattern results in a textured 3D garment. This texture can also be transferred to additional garments by simply changing the latent codes. Textured patterns can also be used to create new garment visuals.
  </div>
  <div class="split_img_if_possible left"><img style="margin:5px; border-radius:10px;" src="/projects/isp/images/sketching.jpg" /></div>
  </div>

  <div class="div_aligned">
    <div class="split_img_if_possible right" ><img style="margin:5px; width:100%;border-radius:10px;" src="/projects/isp/images/modify_panels.jpg" /> 
    </div>
    <div class="split_text_if_possible" style="width: 100%;" >
      We can also easily manipulate the garment 3D shape by editing the panels. Our sewing pattern representation makes it easy to specify new edges by drawing and erasing lines in the 2D panel images, by simply optimizing a 2D Chamfer distance.
    </div>
  </div>

</div>


<h2> BibTeX </h2>
If you find our work useful, please cite it:

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>@article{li2023isp,
  author = {Ren, Li and Guillard, Benoit and Fua, Pascal},
  title = {ISP: Multi-Layered Garment Draping with Implicit Sewing Patterns},
  journal = {Advances in Neural Information Processing Systems},
  year = {2023}
}
</code></pre></div></div>


<hr class="hr_style_thin">

<h3> References and related work</h3>


<div class="div_refs">
  <div class="div_aligned_top">
    <div style="width: 12%; display:inline-block; text-align:right; margin-right:1%;">[<i>MU</i>]</div>
    <div style="width: 87%; display:inline-block;">MeshUDF: Fast and Differentiable Meshing of Unsigned Distance Field Networks, Guillard et al., <i>ECCV</i> 2022.</div>
  </div>
</div>
<div class="div_refs">
  <div class="div_aligned_top">
    <div style="width: 12%; display:inline-block; text-align:right; margin-right:1%;">[<i>AN</i>]</div>
    <div style="width: 87%; display:inline-block;">AtlasNet: A Papier-Mâché Approach to Learning 3D Surface Generation, Groueix et al., <i>CVPR</i> 2018.</div>
  </div>
</div>
<div class="div_refs">
  <div class="div_aligned_top">
    <div style="width: 12%; display:inline-block; text-align:right; margin-right:1%;">[<i>NSM</i>]</div>
    <div style="width: 87%; display:inline-block;">Structure-Preserving 3D Garment Modeling with Neural Sewing Machines, Chen et al., <i>NeurIPS</i> 2022.</div>
  </div>
</div>
