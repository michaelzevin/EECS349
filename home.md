# Predicting Stellar Evolution with Gaussian Process Regression
Michael Zevin
michaelzevin2014@u.northwestern.edu
EECS 349 -- Northwestern University

### Motivation

The evolution of stars is fundamental to many areas of astrophysics, ranging from the formation of planets to evolution of the universe as a whole. 
Simulating the evolution of stars, in particular large populations of stars, is paramount for properly understanding a diverse range of astrophysical processes. 
However, accurately simulating stellar evolution is difficult and computationally expensive, especially when simulating stars that are interacting with one another in a binary system. 
Binary stars are in fact more common than isolated stars, and lead to important transient astrophysical phenomena, such as the merging of black holes, X-ray binary systems, and certain types of supernovae. 
Simulating a dense enough grid of such systems is computationally unfeasible, and the ability to accurately interpolate stellar evolution would be a critical advancement in the study of stellar populations. 

### Methods

In this project, we use Gaussian Process Regression (GPR) to predict the evolution of various physical parameters in binary stellar evolution sequences, such as the temperature of the stars, brightness of the stars, and the rate at which one star transfers mass to another as a funtion of time. 
To train our model, we use a grid of ~1000 simulations of a star transferring mass to a compaion black hole. 
Each simulation is defined by the following initial conditions (i.e. inputs):
- Star mass
- Black hole mass
- Orbital separation
- Metallicity (i.e. the abundance of elements heavier than Helium)

These initial conditions map to a few dozen time dependent outputs, such as the star's luminosity and temperature, the rate at which mass is being transferred from the star to the black hole, and the evolution of the system's orbit. 
We train a GPR model and predict the evolution of systems at points in our 4-dimensional input space at which simulations were not performed. 
In addition to providing interpolated evolutionary sequences, GPR also predicted the uncertainty at any point in our input space. 
This not only allows us to predict the evolution of unsimulated systems, but also allows us to target regions of parameter space where it would be best to spend computational resources to simulate new systems, thereby improving the overall accuracy of our model. 

### Results

To assess the quality of our interpolations, we perform 10-fold cross-validation and calculate the average mean-squared error (MSE) of our interpolations for various output parameters. 
We find errors that are generally as low as a few percent. 
The initial conditions of our simulations (i.e. our input feature) all drastically affect the evolution of the binary systems, and were all important for accurate interpolation. 
Our method also predicts the areas of parameter space with the highest interpolation uncertainty. 
These regions will be targeted with future simulations and once finished will be added to our training set
This will thereby improving the accuracy of our model, and we can continue this process iteratively to build a highly accurate and rapid means for predicting the evolution of stellar systems. 


![Image](images/2d_test_evolution.png)



<img src="images/2d_test_evolution.png" alt="hi" class="inline"/>


### Final Report
[Click here for the full final report.](final_report.md)

##### include interpolation image and MSE image

You can use the [editor on GitHub](https://github.com/mzevin1/EECS349/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/mzevin1/EECS349/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
