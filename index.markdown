---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
<!-- -->
<style>
/* Split the screen in half */
.split {
    display: block;
    height: 100%;
    width: 50%;
  }
  
  /* Control the left side */
.left {
    float:left;
    margin:5px; 
}
  
/* Control the right side */
.right {
    float:right;
    margin:5px; 
}

.small {
	width: 26%; 
	/*width: 32%; */
}

.big {
	width: 68%;
}

</style>

<div>
    <div class="split right small">
        <div>
        <img id="pp" src="/assets/pp.jpg" />
        </div>
    </div>
    <div class="split left big">
    	<h1>Hello!</h1>
        <p>I am Benoît, a 4th year PhD student at <b><a href="http://cvlab.epfl.ch">EPFL’s CvLab</a></b>, supervised by <b><a href="https://people.epfl.ch/pascal.fua/bio?lang=en">Prof. Pascal Fua</a></b>.</p>
        <p>My work is focused on finding good representations for 3D surface reconstruction and manipulation with neural networks. 
        <br>I was lucky to be a research intern at Microsoft Research in 2021 and Meta Reality Labs in 2022.</p>
    </div>
</div>

<div style="clear: both;"> </div>

***

# Publications
*(full list on [scholar](https://scholar.google.com/citations?user=9c5ruhsAAAAJ&hl=en))*

<div>
    <div class="split left small">
        <div>
        <img id="pp" src="/assets/dig.jpg" />
        </div>
    </div>
    <div class="split right big">
    	<h2>DIG: Draping Implicit Garment over the Human Body</h2>
    	<p><a href="https://liren2515.github.io/page/">Ren Li</a>,
        <b>Benoit Guillard</b>, 
        <a href="https://scholar.google.com/citations?user=yz2P_aUAAAAJ&hl=en&oi=ao">Edoardo Remelli</a>,
        <a href="https://scholar.google.com/citations?user=kzFmAkYAAAAJ&hl=en&oi=ao">Pascal Fua</a> ; at ACCV 2022 (Oral)</p>
        <p><b>
        	<a href="https://arxiv.org/abs/2209.10845">[Paper]</a>
        	<a href="https://github.com/liren2515/DIG">[Code]</a>
        </b></p>
        <p>Reconstructing and draping garments over a parametric body model, with neural network trained to avoid collisions.</p>
    </div>
</div>

<div style="clear: both;"> </div>

<div>
    <div class="split left small">
        <div>
        <img id="pp" src="/assets/lidar.jpg" />
        </div>
    </div>
    <div class="split right big">
    	<h2>Learning to Simulate Realistic LiDARs</h2>
        <p><b>Benoit Guillard</b>, 
        <a href="https://scholar.google.com/citations?user=PnaHFhUAAAAJ&hl=en&oi=ao">Sai Vemprala</a>,
        <a href="https://scholar.google.com/citations?user=B3ywvIcAAAAJ&hl=en&oi=ao">Jayesh K. Gupta</a>,
        <a href="https://scholar.google.com/citations?user=Q5CBlNcAAAAJ&hl=en&oi=ao">Ondrej Miksik</a>,
        <a href="https://scholar.google.com/citations?user=E_UlAVQAAAAJ&hl=en&oi=ao">Vibhav Vineet</a>,
        <a href="https://scholar.google.com/citations?user=kzFmAkYAAAAJ&hl=en&oi=ao">Pascal Fua</a>,
        <a href="https://scholar.google.com/citations?user=4D1n8scAAAAJ&hl=en&oi=ao">Ashish Kapoor</a> ; at IROS 2022</p>
        <p><b>
        	<a href="https://www.microsoft.com/en-us/research/group/autonomous-systems-group-robotics/articles/data-driven-sensor-simulation-for-realistic-lidars/">[Blog Post]</a>
        	<a href="https://arxiv.org/abs/2209.10986">[Paper]</a>
        	<a href="https://youtu.be/Vd0UsiXEoFA">[Video]</a>
        </b></p>
        <p>A neural network to simulate how objects interact with LiDARs given their appearance, deployed to a standard driving simulator.</p>
    </div>
</div>

<div style="clear: both;"> </div>

<div>
    <div class="split left small">
        <div>
        <img id="pp" src="/assets/meshudf.jpg" />
        </div>
    </div>
    <div class="split right big">
    	<h2>MeshUDF: Fast and Differentiable Meshing of Unsigned Distance Field Networks</h2>
        <p><b>Benoit Guillard</b>, 
        <a href="https://scholar.google.com/citations?user=UxEI4sQAAAAJ&hl=en&oi=ao">Federico Stella</a>,
        <a href="https://scholar.google.com/citations?user=kzFmAkYAAAAJ&hl=en&oi=ao">Pascal Fua</a> ; at ECCV 2022</p>
        <p><b>
        	<a href="./meshudf/">[Project Page]</a>
        	<a href="https://arxiv.org/abs/2111.14549">[Paper]</a>
        	<a href="https://github.com/cvlab-epfl/MeshUDF">[Code]</a>
        </b></p>
        <p>An extension of Marching Cubes to mesh non-watertight surfaces, applied the output of Unsigned Distance Field networks. We also derive gradients for the reconstructed vertex positions wrt. the UDF field.</p>
    </div>
</div>

<div style="clear: both;"> </div>

<div>
    <div class="split left small">
        <div>
        <img id="pp" src="/assets/sketch2mesh.gif" />
        </div>
    </div>
    <div class="split right big">
    	<h2>Sketch2Mesh: Reconstructing and Editing 3D Shapes from Sketches</h2>
        <p><b>Benoit Guillard</b><sup>*</sup>, 
        <a href="https://scholar.google.com/citations?user=yz2P_aUAAAAJ&hl=en&oi=ao">Edoardo Remelli</a><sup>*</sup>,
        <a href="https://www.linkedin.com/in/pierre-yvernay-838a2016a/">Pierre Yvernay</a>,
        <a href="https://scholar.google.com/citations?user=kzFmAkYAAAAJ&hl=en&oi=ao">Pascal Fua</a> ; at ICCV 2021
      	<i>( <sup>*</sup> indicates equal contributions)</i></p>
        <p><b>
        	<a href="https://arxiv.org/abs/2104.00482">[Paper]</a>
        	<a href="https://github.com/cvlab-epfl/sketch2mesh">[Code]</a>
        </b></p>
        <p>A deep learning based pipeline to reconstruct and locally edit 3D shapes from sketches.</p>
    </div>
</div>

<div style="clear: both;"> </div>

<div>
    <div class="split left small">
        <div>
        <img id="pp" src="/assets/uclidnet.jpg" />
        </div>
    </div>
    <div class="split right big">
    	<h2>UCLID-Net: Single View Reconstruction in Object Space</h2>
        <p><b>Benoit Guillard</b>, 
        <a href="https://scholar.google.com/citations?user=yz2P_aUAAAAJ&hl=en&oi=ao">Edoardo Remelli</a>,
        <a href="https://scholar.google.com/citations?user=kzFmAkYAAAAJ&hl=en&oi=ao">Pascal Fua</a> ; at NeurIPS 2020</p>
        <p><b>
        	<a href="https://arxiv.org/abs/2006.03817">[Paper]</a>
        	<a href="https://github.com/cvlab-epfl/UCLID-Net">[Code]</a>
        </b></p>
        <p>A network architecture mixing 3D convolutions and local surface patches for reconstructing object from a single image.</p>
    </div>
</div>
<div style="clear: both;"> </div>
<br>

***
# Past, unpublished work

<div>
    <div class="split left small">
        <div>
        <img id="pp" src="/assets/scamp.jpg" />
        </div>
    </div>
    <div class="split right big">
        <h2>AnalogNet: Convolutional Neural Network Inference on Analog Focal Plane Sensor Processors</h2>
        <p><a href="https://scholar.google.com/citations?user=KsuL4YgAAAAJ&hl=en">Matthew Z Wong</a><sup>*</sup>,
        <b>Benoit Guillard</b><sup>*</sup>, 
        <a href="https://rmurai.co.uk/">Riku Murai</a>, 
        <a href="https://www.sajad-saeedi.ca/">Sajad Saeedi</a>, 
        <a href="https://www.doc.ic.ac.uk/~phjk/">Paul Kelly</a>
        <i>( <sup>*</sup> indicates equal contributions)</i></p>
        <p><b>
            <a href="https://arxiv.org/abs/2209.10845">[arXiv]</a>
            <a href="https://www.imperial.ac.uk/media/imperial-college/faculty-of-engineering/computing/public/1819-pg-projects/Optimising-convolutional-neural-networks-for-super-fast-inference-on-focal-plane-sensor-processor-arrays.pdf">[Master thesis]</a>
        </b></p>
        <p>A low-level and super lightweight CNN implementation running directly on the analog light sensor of a special camera, <a href="https://personalpages.manchester.ac.uk/staff/p.dudek/scamp/">SCAMP5</a>.</p>
    </div>
</div>

<div style="clear: both;"> </div>
<br>

***
# Academic services
I was a reviewer for CVPR (2022 best reviewer award), ICCV, ECCV, ACCV, NeurIPS (2022 top reviewer), ICLR, ICML, C&G.