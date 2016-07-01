# Middleman V4 with Contentful Middleman Example
I've come to rely quite heavily on Middleman and Contentful in my workflow. The documentation for the latter assumes a certain technical ability. I'm a desginer by trade, and while I'm decent at the front-end, there was a big learning curve for me on the Middleman/Contentful integration. By now I'm becoming pretty comfortable with it (or at least, a lot better than I was).

This might help other people. It's using Middleman V4 and the beta Contentful Middleman gem.

I prefer Slim (quite a bit) over ERB, so you'll need that gem. Sass or Scss doesn't matter, I prefer the Sass indented syntax, but you can use either or mix and match.

This mainly exists to show you how to do a few key things, but in production, you're obviously going to do a few things differently.

----

## Start It Up
1. `bundle install`
1. create a `.env` file at the root and use something like this: `CONTENTFUL_TOKEN='your-token-here'`
1. In the `config.rb` file, change your space and content types.
1. `middleman-contentful`
1. `middleman-server`

----

## Other Things of Interest
### Hosting
Netlify is a great webhost and works flawlessly with the contentful_middleman gem. Essentially, you can tell it to rebuild every time you push a new version to Github or your client adds new content.

### Other Options
The contentful_middleman gem is great for a lot of reasons (including being able to produce dynamic pages like you'd want in a blog). If you just need minor snippets of content though (and you're not doing new dynamicallly created pages), you might want to import Contentful data via Angular. It's a 10-15 second wait before you see new content vs the 1-5 minutes it takes Netlify to push a new build.

### Potential Issues
You might have trouble with the bundle install, specifically with eventmachine, [this](https://github.com/eventmachine/eventmachine/issues/643) might help.

### Ignore Your Data Folder
I don't like having new data junk up my git commits, also don't like having the lack of data bork MM. If you're going to want this to run independant of an existing data folder, you'll like this little snippet: `if Dir.exist?(config.data_dir)`

### Alias Stuff
I'm lazy. In my .bash_profile I alias a few things that I use all the time:

```sh
alias mm='bundle exec middleman server'
alias mm-build='bundle exec middleman build'
alias mm-content='bundle exec middleman contentful'
```
