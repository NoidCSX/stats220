# This is the meme I made
I made this using R and the package [Magick](https://cran.r-project.org/web/packages/magick/vignettes/intro.html).
![my_meme](https://user-images.githubusercontent.com/101961367/159162311-e78f521c-1aba-407e-9031-bc52b6daa9d2.png)

# What went into this meme
I found some *funny* images I had on my computer and threw them into R, to create a top text bottom text meme, a very common meme format with my own take of **Comic Sans** text.
```
**To Create this I used**
- Simpsons Image
- Cat Image
```
The [Simpsons Picture](https://i.imgur.com/Olevan8.jpg)![Simp](https://i.imgur.com/Olevan8.jpg)

# Here I am going to Waffle to get my assinment marks :shipit:
1. WOW THIS IS
2. ORDERED BULLET POINTS!!!

- UNORDERED POINTS!!!!
- Linking [Other Sites (Reddit)](https://www.reddit.com/)

# My R Code used to create the meme (In fencing?)

```
library(magick)

#Top image
crying_cat <- image_read(path = "https://i.imgur.com/2JhTthE_d.webp?maxwidth=760&fidelity=grand") %>%
  image_scale(500)

#Top Text
top_text <- image_blank(width = 500, 
                             height = 370, 
                             color = "#000000") %>%
  image_annotate(text = "Me\nin\nlectures",
                 color = "#FFFFFF",
                 size = 60,
                 font = "Comic Sans",
                 gravity = "center")
#Bottom Image
ralph_nose <- image_read(path = "https://i.imgur.com/Vf7WYUk_d.webp?maxwidth=760&fidelity=grand") %>%
  image_scale(500)

#Bottom Text
bot_text <- image_blank(width = 500, 
                             height = 370, 
                             color = "#000000") %>%
  image_annotate(text = " Also\nMe\nin\nlectures",
                 color = "#FFFFFF",
                 size = 60,
                 font = "Comic Sans",
                 gravity = "center")
#Top Square
top_row <- c(crying_cat, top_text) %>%
image_append()

#Bot Square
bot_row <- c(ralph_nose, bot_text) %>%
image_append()

meme  <-  c(top_row, bot_row) %>%
  image_append(stack = T)

image_write(meme, "my_meme.png")
```
