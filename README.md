# guardiannews

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

###Describe and justify some of the key decisions you made in your project. Why did you
###decide to do what you did? How does your choice compare to the alternatives?

Firstly I picked my API, it took me longer than I had hoped to find something interesting
with a good amount of usable detail.  I went for the Guardian api as it provides a good
end point that allowed me to access stories and images which I knew I would be able to
produce something appealing with.

After this I drew a wireframe so that I had a clear image of what I was working towards
and which parts of the app could be constructed using components.  This allowed me to
get set up quickly with the basics of the app and ensured I wasn't going to miss anything.

I think the choices I made right at the start really helped me with this app. Had I done
no planning I would have just been building components blindly without any real idea of
what I was working towards.

I did consider splitting the article components in two, one for the image and one for
the title/text.  I decided against this because I didn't see them being needed
separately in this app but looking back it may be useful for someone in the future
working on it to have access to them separately.


###Describe in detail a few things you would have done differently if starting again. What
###was your rationale that led to the initial decision? What made you realise that a different
###option would have been a better choice? Why do you believe it to be a better choice?

If I was starting again I would build my components so that they were passed only the necessary
elements from my article objects.  This way if you wanted to incorporate an api from another
news/blog site the components would be entirely reusable, at the moment objects from another
api would have to be structured in the exact same way as the Guardian api.  When I started the
project I was only considering the single api which lead me down a slightly narrower path with
regards to scope for adding to the project.  

###Describe in detail a few things you would have done had you more time. How would this
###addition/change benefit the application? What negative impact, if any, does its absence
###have on the application?

The first thing I would do is write some tests.  At the moment the app is small and not very
complex but if you were to add additional api's for improved search results it could easily
start to go wrong without testing.  

The modal for viewing the full article doesn't work exactly as I would like it to either.  The
positioning isn't ideal and I would like to be able to click on the screen around it and
for the modal to close.  This is making it a slightly less enjoyable user experience, having to
scroll to the end of the article isn't great if you don't want to read it.

I would also tidy up the css, I'm not completely happy with the positioning of some of article
cards and image can some time change depending on it's size which makes it look a bit untidy.  
I would also like to add some additional search functionality to incorporate dates, at the
moment some of the articles appearing are quite old.


N.B

App deployed using Heroku at https://guardain-news.herokuapp.com/
