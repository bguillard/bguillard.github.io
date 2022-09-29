---
layout: project
title: "MeshUDF"
permalink: /meshudf/
description: MeshUDF Fast and Differentiable Meshing of Unsigned Distance Field Networks

---
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
    <div class="div_rounded_corners" ><p style="color: #fdfdfd;">
        <svg class="svg-icon"><use xlink:href="{{ 'assets/minima-social-icons.svg#github' | relative_url }}"></use></svg>
        <a href="https://github.com/cvlab-epfl/MeshUDF" style="color: #fdfdfd;">Code</a>
    </p></div>
</div>

<div class="centered_div big">
 <iframe width="800" height="450" src="https://www.youtube.com/embed/TVMwnazd9lQ" frameborder="0"></iframe> 
</div>


<div class="div_text">
	<h1 style="text-align: center;">Abstract</h1>
	Unsigned Distance Fields (UDFs) can be used to represent non-watertight surfaces. However, current approaches to converting them into explicit meshes tend to either be expensive or to degrade the accuracy. Here, we extend the marching cube algorithm to handle UDFs, both fast and accurately. Moreover, our approach to surface extraction is differentiable, which is key to using pretrained UDF networks to fit sparse data.
</div>


<hr class="hr_style">
