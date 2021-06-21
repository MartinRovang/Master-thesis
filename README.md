<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->

<!--
[![Contributors][contributors-shield]][contributors-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
-->




<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/CRAI-OUS/WMH-Segmentation">
    <img src="images/logo_new.jpg" alt="Logo" width="766" height="494">
  </a>

  <h3 align="center">WMH segmentation</h3>

  <p align="center">
    WMH segmentation using FLAIR and/or T1 on MR volumes
    <br />
    <a href="https://github.com/CRAI-OUS/WMH-Segmentation"><strong>Explore the docs »</strong></a><br>
    <a href="https://github.com/CRAI-OUS/WMH-Segmentation/blob/main/main.pdf"><strong>Master thesis »</strong></a>
    <br />
    <br />
    <a href="https://github.com/CRAI-OUS/WMH-Segmentation/issues">Report Bug</a>
    ·
    <a href="https://github.com/CRAI-OUS/WMH-Segmentation/issues">Request Feature</a>
  </p>
</p>


<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#API-usage">API Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

My code for master thesis, predicting WMH on MR FLAIR and/or T1 volumes.


### Built With

This section lists any major frameworks that is used to build the project.
* Python
* Pytorch



<!-- GETTING STARTED -->
## Getting Started

# Option 1

1) Download Latest build and follow steps below for prediction:
2) Extract the attention model from the models folder
3) Load best_params_attention.pt from the weights folder
4) When predicting make sure the input is [N, C, H, W] (AND MUST BE Z-STANDARDIZED OVER PATIENT VOLUME!!) where N is the number of slices and channel are (flair, flair, T1)(3), H is heights, and W is width. For optimal result use sagital plane
5) Attention model outputs prediction map, attention maps and average pooled maps: 
`pred_mask, up4_deep_out, up3_deep_out, up2_deep_out,up1_deep_out, psi_out4, psi_out3, psi_out2, psi_out1 = model(input) # IF ATTENTION.`
If only interested in prediction this can be used instead: `pred_mask, *rest = model(input)`

# Option 2

Download Latest build and follow steps below for prediction:

1) Make sure you have the required package
To avoid conflicts make a new virtual environment.
> `conda install -y -c pytorch pytorch torchvision`
> `conda install -y -c conda-forge numpy matplotlib scikit-learn scikit-image nibabel numba rich`
> `pip3 install kornia`

2) The data should be in one folder (for instance /data) and have patient folders as shown below (.gz files): 

![alt text](https://i.imgur.com/XlX7vpK.png)

In each patients the files should be as follows: 

![alt text](https://i.imgur.com/vF0U2d6.png)

3) Insert path in config.py @ model_save_path = 'path1/path2/weight.pt' to load weights.

4) Prediction is done with the command `python main.py -p path`, path should be the data folder to predict.

5) Prediction are named `pred_mask.nii.gz` and there should be one in every patient folder.

## Warning:
If there is no T1.nii.gz or FLAIR.nii.gz in the patient folder there wont be any prediction


### Installation

********


<!-- USAGE EXAMPLES -->
## Usage

*****



<!-- ROADMAP -->
## Roadmap

See the [open issues](https://github.com/CRAI-OUS/WMH-Segmentation/issues) for a list of proposed features (and known issues).




## API Usage

API has been implemented, mostly for test purposes.

#### ENDPOINTS:

`POST /api/files/<id>/predict

GET DELETE POST /api/files

GET /api/files/<id>/report
`
#### Examples:

`file=@<path_to_files>` -> `file=@somefolder/example1_folder/FLAIR.nii.gz`

Upload volume ->  `curl -F file=@<path_to_files> localhost:5000/api/files` RESPONSE -> {'id': UUID} OK

Start prediction on ID ->  `curl -X POST localhost:5000/api/files/<id>/predict` RESPONSE -> OK

Download pdf report ->  `curl -X GET localhost:5000/api/files/<id>/report --output report.pdf`

<!-- CONTRIBUTING 
NOTE: For best performance the volume has to be in the orientation as the trained data, this orientation is ('L', 'A', 'S').
If the examples in the report is not in the same view as image below it is most likely wrong input.-->

![image](https://user-images.githubusercontent.com/24882057/116706588-12e09f80-a9ce-11eb-8c7d-1c26de61b24b.png)



<!-- CONTRIBUTING -->
## Contributing

*******


<!-- LICENSE -->
## License

****



<!-- CONTACT -->
## Contact

[@Martinrovang](https://twitter.com/Martinrovang) - martinrovang@gmail.com

Project Link: [https://github.com/CRAI-OUS/WMH-Segmentation](https://github.com/CRAI-OUS/WMH-Segmentation)



<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
* [GitHub Emoji Cheat Sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet)
* [Img Shields](https://shields.io)
* [Choose an Open Source License](https://choosealicense.com)
* [GitHub Pages](https://pages.github.com)
* [Animate.css](https://daneden.github.io/animate.css)
* [Loaders.css](https://connoratherton.com/loaders)
* [Slick Carousel](https://kenwheeler.github.io/slick)
* [Smooth Scroll](https://github.com/cferdinandi/smooth-scroll)
* [Sticky Kit](http://leafo.net/sticky-kit)
* [JVectorMap](http://jvectormap.com)
* [Font Awesome](https://fontawesome.com)





<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/CRAI-OUS/WMH-Segmentation/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=for-the-badge
[forks-url]: https://github.com/othneildrew/Best-README-Template/network/members
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=for-the-badge
[stars-url]: https://github.com/CRAI-OUS/WMH-Segmentation/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=for-the-badge
[issues-url]: https://github.com/CRAI-OUS/WMH-Segmentation/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/othneildrew/Best-README-Template/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/othneildrew
[product-screenshot]: images/screenshot.png
