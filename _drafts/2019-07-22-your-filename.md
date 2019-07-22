---
published: false
---
>For the last post, we use a tableau-like GUI addin function to explore the data and create an informative plot. 

## Lets summary the pro of using this tool:
### Pro: 
1. You shorten the learning curve and are making presentable plot on day one, you can learn when actually make an impact in your assigned job.
2. You learn to code by using tools similar to Tableau.
3. You can easily speed up the data exploration and cleaning stage. Remember to used facet, fill, to create 3 to 4 dimension plot. 
4. Again, You are creating 3 to 4 dimension plot with almost coding free, this eliminate the chance of making mistakes for new user. 

Now here comes another add-in function that can change the plot above to the one below this without much coding…

The add-in function is called "ggThemeAssist". Before you open the window, you need to highlight a ggplot object, then you would open this window the same way as you did for the last one. Similarly, after complete the editing, the code used will be saved for future used. Here is the plot I created using ggThemeAssist.

    # I would suggest you read the last related post to get the most from this one
    # third plot further edit by packages (no code written by myself) 

        plot2 +
            theme(plot.subtitle = element_text(size = 12), 
                axis.text.y = element_text(size = 15, angle = 45), 
                panel.background = element_rect(fill = "burlywood"), 
                plot.background = element_rect(fill = "blanchedalmond"), 
                legend.key = element_rect(fill = "burlywood"), 
                legend.background = element_rect(fill = "burlywood")) +
            labs(title = "Reports for Cars", size = "Size", 
            subtitle = "The count of record groupped by driving power (drv) and (tran), coloring by (fl). The table excluded the munual cars and only look at auto car. ")
        Meanwhile, I would recommend you to use a consistent graphing theme for all the plots you plan to present. To do so, you can do something like this below：
        my_theme <- 
         theme(plot.subtitle = element_text(size = 12), 
                axis.text.y = element_text(size = 15, angle = 45), 
                panel.background = element_rect(fill = "burlywood"), 
                plot.background = element_rect(fill = "blanchedalmond"), 
                legend.key = element_rect(fill = "burlywood"), 
                legend.background = element_rect(fill = "burlywood"))
        #copy theme() part only



      #first plot made by the packages
      first_p <- ggplot(data = mpg) +
          aes(x = trans, y = drv, fill = fl) +
          geom_tile() +
          facet_wrap(vars(trans))



    first_p + my_theme
    #this will apply the same theme to the plot and keep your other plot look as consistant as the last one

From ThisTo ThisOf course, if you do not like any theme you made by yourself or you are extremely lazy. You can always download packages like ggthemes or ggtech that include many predefined theme for you to use. The package also provides some extra color and fill to choose from. 
However, doing everything without actually coding seen too good to be the truth, what are we missing in creating a professional plot? It is the annotation. The well-written ggplot should also include annotation that further highlight the information in the plot. This function can only be created in my current knowledge. Therefore, a well-written ggplot should look something like this
ggplot (data = <DATA>  ) +
<GEOM_FUNCTION>  (mapping = aes( <MAPPINGS>  ),
stat =  <STAT> , position = <POSITION> ) +
<COORDINATE_FUNCTION> +
<SCALE_FUNCTION> +
<THEME_FUNCTION>
Let's summarize what we have done and how we can learn ggplot as we are making this plot. 
The <DATA> and <GEOM_FUNCTION> are required; the <FACET_FUNCTION>, <SCALE_FUNCTION> functions are optional but recommended; the <THEME_FUNCTION> are needed for better business images. The <COORDINATE_FUNCTION> is optional.
