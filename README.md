# Open data and reproducibility: R Markdown, dashboards and Binder

A workshop at the UK Cognitive Linguistics Conference, on 26 July 2020 (https://www.ukclc2020.com/pre-conference), led by Pablo Bernabeu and Eirini Zormpa.
 
The methods for disseminating research in cognitive linguistics, and other fields, are advancing. Papers now include more and more supplementary materials. This shift has been facilitated by burgeoning technologies and available training. Another major contributor was the replication crisis in psychology. Nowadays, researchers customarily examine the extra materials with new studies. These materials are available to non-academics, too. Newer tools are available, notably based on open-source software. Let’s look at three tools around the R language.

[The sections and times were adjusted during the workshop.]

You’re welcome to post any questions in [issues](https://github.com/pablobernabeu/UKCLC2020-workshop-Open-data-and-reproducibility/issues).

<br>


## **R Markdown** &nbsp; `75 min`

Keep your input and output in check using R Markdown (https://rmarkdown.rstudio.com/).

Examples: https://bookdown.org/yihui/rmarkdown/journals.html,  http://rpubs.com/

### Text styling with Markdown, HTML and CSS &nbsp; `30 min`

- **Background** 

    - https://rmarkdown.rstudio.com/authoring_pandoc_markdown.html
    - https://html.com/

- **Live demo**: Pablo & Eirini, 20 minutes
        
    Writing a text showcasing markup styles such as italics, bold, indentation, hyperlinks, maths, styled inline code, styled code chunk.

- **Task**: Replicating, 10 minutes

   - Replicate a [model document](https://en.wikipedia.org/wiki/Markdown) using some of the markup features presented before. You can also try to incorporate other features that you can find at https://rmarkdown.rstudio.com/authoring_pandoc_markdown.html. 
   - Replicate another [model document](https://github.com/pablobernabeu/UKCLC2020-workshop-Open-data-and-reproducibility/blob/master/R%20Markdown/example%20of%20HTML%20and%20CSS%20use.png).

    
### Running code &nbsp; `15 min`

- **Background:** https://rmarkdown.rstudio.com/lesson-4.html, https://rmarkdown.rstudio.com/lesson-3.html (basics); https://yihui.org/knitr/options/ (advanced)

- **Live demo:** Eirini , 10 minutes

    - Inline code and code chunks (#comments allowed in both)
    - Options for each type: limited options for inline code (e.g., no plots or tables), numerous options for code chunks (knitr options)

- **Task:** Debugging, 5 minutes (extra time added)

    - Debugging an R Markdown document such that it knits successfully! This document can be found [here](https://github.com/pablobernabeu/UKCLC2020-workshop-Open-data-and-reproducibility/blob/master/R%20Markdown/bugs.Rmd).
    - Replicating a doc from rpubs.com, for instance, https://rpubs.com/AlexandreV/643078 (ideal because it has accessible data--thanks to Jing!!)
    
        
### Cross-references &nbsp; `10 min`

- **Background** 

    - https://bookdown.org/yihui/rmarkdown-cookbook/cross-ref.html

- **Live demo**: Pablo, 5 minutes
        
    Using this for figures and tables.

- **Task**: Modifying code, 5 minutes

    Create a standard R Markdown document in RStudio, turn the `summary()` into a table by wrapping it in `knitr::kable()`, add cross-references to the table and the plot, and knit (please retry any of those steps and ask us any questions if necessary).
    
    
### Creating a paper &nbsp; `10 min`

- **Background:** https://github.com/rstudio/rticles

- **Live demo:** Pablo, 5 minutes

- **Task:** Free creation, 5 minutes
    
    
### Publishing to RPubs &nbsp; `10 min`

- **Background:** https://rpubs.com/ 

- **Live demo:** Pablo, 5 minutes

- **Task:** Free creation, 5 minutes

<br>


## **Dashboards and web applications** &nbsp; `55 min`

On a further step in reproducible, open data, we will learn how to publish dashboards online presenting data in the form of plots and tables. These all-reproducible dashboards are displayed as websites; thus, they can include hyperlinks and downloadable files. Some of the R packages used are ‘rmarkdown,' ‘knitr,’ ‘ggplot,’ ‘plotly,’ ‘flexdashboard,’ and ‘shiny.’ The aim is to practise with different forms of dashboards (Flexdashboard, Shiny, Flexdashboard-Shiny) and the suitable hosting platforms (personal website, RPubs, Binder, Shinyapps, and custom servers).

Examples: 
https://pablobernabeu.shinyapps.io/Dutch-modality-exclusivity-norms/
https://pablobernabeu.shinyapps.io/ERP-waveform-visualization_CMS-experiment/
https://pablo-bernabeu.shinyapps.io/experimental-data-simulation/
https://shiny.rstudio.com/gallery/
https://rmarkdown.rstudio.com/flexdashboard/examples.html

### Creating a Flexdashboard (interactive R Markdown) &nbsp; `20 min`

- **Background:** https://rmarkdown.rstudio.com/flexdashboard/

- **Live demo:** Pablo, 10 minutes

- **Task:** 10 minutes

    Create a flexdashboard document and use ggplotly() from plotly package
    
    ```
    df <- data.frame(
    gp = factor(rep(letters[1:3], each = 10)),
      y = rnorm(30)
    )
    ds <- do.call(rbind, lapply(split(df, df$gp), function(d) {
      data.frame(mean = mean(d$y), sd = sd(d$y), gp = d$gp)
    }))

    # The summary data frame ds is used to plot larger red points on top
    # of the raw data. Note that we don't need to supply `data` or `mapping`
    # in each layer because the defaults from ggplot() are used.
    ggplotly(ggplot(df, aes(gp, y)) +
      geom_point() +
      geom_point(data = ds, aes(y = mean), colour = 'red', size = 3))
    ```
    
    and kable() from knitr package (see also [DT package](https://rstudio.github.io/DT/))
    
    ```
    kable(summary(cars))
    ```
    

### Creating a web application using Shiny &nbsp; `10 min`

- **Background:** https://shiny.rstudio.com/

- **Live demo:** Pablo, 5 minutes

- **Task:** 5 minutes
    
    Look into this web application, find where the tabs are created in the code, remove one of those, and create another one: https://pablobernabeu.shinyapps.io/ERP-waveform-visualization_CMS-experiment/
    

### Combining Flexdashsboard and Shiny for best results &nbsp; `15 min`

- **Background:** https://rmarkdown.rstudio.com/flexdashboard/shiny.html

- **Live demo:** Pablo, 5 minutes

- **Task:** Modify [some of this app](https://github.com/pablobernabeu/Dutch-modality-exclusivity-norms-Bernabeu-2018/blob/master/Shiny-app/index.Rmd), 10 minutes



### Publishing to shinyapps.io &nbsp; `10 min`

- **Background:** https://www.shinyapps.io/

- **Live demo:** Pablo, 5 minutes

- **Task:** Sign up and deploy application, 5 minutes

<br>


## **Binder** &nbsp; `15 min`

Did you know that you can enable public access to your data and analysis code in RStudio, on a simple internet browser? There are various options for this, and one of the most accessible ones is Binder (https://mybinder.org). We’ll look at Binder’s requirements and possibilities.

RStudio environment example: http://mybinder.org/v2/gh/binder-examples/r/master?urlpath=rstudio
Dashboard environment example: https://mybinder.org/v2/gh/pablobernabeu/Modality-switch-effects-emerge-early-and-increase-throughout-conceptual-processing/3863a3bfa79a4f765f3dac39007802b6f5e2bd9d?urlpath=shiny/Shiny-app/

### Creating a Binder repo for R coding &nbsp; `15 min`

- **Background:** 
    - https://github.com/binder-examples/r/blob/58b719735aa0be4938079890151cfc8934dcec60/README.md
    - https://mybinder.org/

- **Live demo:** Eirini, 10 minutes

    How to enable web-based environments for an RStudio instance and a Shiny app.

- **Task:** Creating runtime.txt and install.R files, adding those to a GitHub repo (a fork of [this one](https://github.com/eirini-zormpa/slow-naming)), creating the Binder repo on mybinder.org, and accessing the RStudio and Shiny environments by editing the URL address [as specified here](https://github.com/binder-examples/r/blob/3fdd90b2c359f249f1707174df0556d48b7d47ef/README.md).

    For install.R file:
    
    ```
    install.packages("rio")
    install.packages("dplyr")
    install.packages("tidyr")
    install.packages("stringr")
    install.packages("ggplot2")
    install.packages("ggridges")
    install.packages("lme4")
    install.packages("lattice")
    install.packages("ggpubr")
    install.packages("wesanderson")
    ```
    
    For runtime.txt file: `r-2020-07-26`
    
<br>

The timing includes a 10-minute introduction, two 10-minute breaks and a 5-minute conclusion.

Real data and code of varying complexity will be used. Basic and advanced R users are welcome. 

Please sign up to RStudio Cloud (https://rstudio.cloud/), which may become useful if you encounter any issues in your local R.

Also suggested: 

installing or updating R (https://www.r-project.org/) and RStudio (https://rstudio.com/products/rstudio/download/);
perusing the links here;
having some data and R code ready, preferably in a Github repository.
