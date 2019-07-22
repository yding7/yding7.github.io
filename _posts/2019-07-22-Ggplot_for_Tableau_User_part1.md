---
published: false
---
"Today, we wil use a tableau-like GUI addin function to explore the data and create an informative plot."

## My Early Expereince We Ggplot

After reading this blog I hope you can be as confident as me in starting with ggplot, even if you have zero coding experience…


It takes more than a year for me to decide to learn ggplots.(obviously, I regret that I did not start learning earlier) I knew these packages a year ago from the basic introduction of tidyverse packages, and I do use it once a while. 

I do need plotting skills to get the job done, but I keep rely on Tableau.

Besides, the main resistance to learn ggplot is its unique plotting language (i guess this can be a pro and con). I did not know where to start. So today, I will introduce the packages that will speed up the learning path for ggplot and design for Tableau heavy-user and non-coder. 

### Let's start:

    > 

    #ggplot
    install.packages(tidyverse) 
    #interative tools for exploring data with ggplot
    install.packages(esquisse)
    #interative tools for making advance edit on ggplot object


    > 



### Data use:
    > 
    mpg <- ggplot2::mpg
    > 

let's imagine a case where you are asked to explore some categorical variables. What should you do? First, you should check the data dictionary to understand the definition of each column and build some conceptual knowledge. So later when you are creating the plot fast, you can easily tell the story behind the plot. You can also do a quick check on the data frame using the functions like summary or glimpse. When you are ready, **open the esquisse GUI tool to build the visuization**.The easiest way to open the tool in Rstudio is go to Tools -> Addins -> browser, then click esquisse inside the pop-up window.

After you click Execute, you should see a pop-up window like this:
![start_esquisse]({{site.baseurl}}/_posts/ggplot_1 .png)


The pop-up window is a GUI that works very like a Tableau. Any Tableau user will quickly master this very soon. The idea of providing a GUI is so GREAT. However, because there are got many limitation of using this GUI. 

some may assume that today we do not need to write a single code to make a great plot. Well, the answer is actually NO. 

Esquisse is a great tool to jumpstart your ability to do things with ggplot2 and data exploration, but not for making the final visuialization. The main benefit is using the drag and drop to create fast plot; however, there are flaws and limit to in this open-sources tool.

## How to use esquisse
Here is how I suggest to use Esquisse in order to get the most out of it:
1. Try to use in the explortory stage, and experience the power of ggplot 
2. Do step-by-step changes and click on "</> Export & code" to check how to code is written
3. Constrate one learning about the geom_ functions in ggplot, don't take too much too on creating labels and theme.
3. Don't be satisfied with the visualization create by the plot. Remember that you should also edit the plot mannually with code. 

### Some bug(find in June 2019):
There are some build-in filter function inside ("choose date"). But these will not been save as code. These harm the ability to replicate the process. In other words, the code provides by the esquisse does not capture the filter process. The code provided cannot replicate the same graph and may not be able to show the code for data cleaning as well as advance ggplot setting.


In addition, the current version of esquisse does not provide the function to build the bubble plot I mentioned in the early post. I would definitely prefer the bubble plots because it will show more information. The current plot (provides below) does not show information on the distribution and frequency of each group. 
#image need

### Demostrating:
So let's say after trying some combinations you decide to create a graph shown in the ggplot2 builder window. Click </> Export & code. You can either Insert code in script or copy to clipboard to save the code to generate the plot. 


    > 
    
ggplot(data = mpg) +   aes(x = model, y = drv, fill = fl) +   
       geom_tile() +   
       theme_minimal() +   
       facet_wrap(vars(trans))
 
    >  
   
Remember when you keep making changes to your plot, the code shown under </> Export & code will change consistently. You can explore the syntax and language on your own, and understand the overall pattern, plus the use of color, fill, facet. 


I have to edit the code copy in the clipboard to actually make the plot I want:

#second plot made by me
    > 
    '%notin%' <- Negate('%in%')
    # my %notin% fucntion work the same as !(trans %in% c('manual(m5)','manual(m6)'))
    >

    >
    mpg2 <- mpg %>% filter(trans %notin% c('manual(m5)','manual(m6)'))
    plot2<-
    ggplot(data = mpg2) +
    aes(x = trans, y = drv,color = fl) +
    geom_count(stat = "sum") +
    scale_fill_brewer(palette = "Spectral") +
    facet_wrap(vars(trans)) +
    scale_size(range=c(2, 15)) +
    theme(axis.text.x = element_text(angle = 90, hjust = 1));plot2
    >
    
#Check out my previous post to learn more about the bubble plot for discrete vs discrete variable

Now, the plot are more informative and present the distribution by the size of the bubble. Please keep in mind that the bubble here actually dot, and we use "color" instead of "fill" to define what the color representing.

# difference: color and fill
    >
    > ggplot(data = mpg) +   
    aes(x = model, y = drv, fill = fl) +   
    geom_tile()
    > ggplot(data = mpg2) +
    aes(x = trans, y = drv, color = fl) +
    geom_count(stat = "sum")
   
The plot looks great, but I would not want to show report the plot. Now here comes another add-in function …

To be continued…


#The example present used the knowledge of creating a dot plot for discrete vs discrete post-post. check it out before or after reading this blog.

#Here I am using Rstudio as my IDE, You may also need to use Rstudio to follow my step
