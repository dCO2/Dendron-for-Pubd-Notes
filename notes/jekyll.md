---
id: 7ez4blt4kt7w9a7ybj2q6pf
title: jekyll
desc: ''
updated: 1698073280702
created: 1698072348067
---

- ![[what i expect from exposés on technologies#^anchor-tech-get-started]]
- jekyll is a static site generator, run in the terminal.
- built with Ruby
- how is jekyll different from [[ReactJs]]?
- [[routing|handling website routes]] is handled using the basic directory structure. that is there is a physical directory for the route; "https://www.example.app/2021/08/21/abcde.md", for example, even though that file intially sat in a *_posts* folder before building. the function that handles this path-generation is hidden, in the jekyll executable, from the user. [[whereas in React|Reactjs]]
- it receives templated (static-)HTML/CSS/JS files and outputs a fully-formed website
- jekyll handles an array of content-data like posts like this:
  - a directory in the build-tree is named as follows _posts. and the page with some collection of posts has, for example, the code: 
    ```html
    {% for post in site.posts %}
        {% if post.layout == 'note' %}
            <div class=post>
                <h1 class=title><a href="{{ post.url }}">{{ post.title }}</a></h1>
                {% if post.feature %}
                <p class=feature-image>
                    <img src="{{ post.feature-image }}"/>
                </p>
                {% endif %}
                <div class=content>
                </div>
                {% include post-meta.html %}
            </div>
        {% endif %}
    {% endfor %}
    ```
- it is deployed to netlfy with the build command: pass
- installing ruby, gem, jekyll for local build: https://stackoverflow.com/questions/37720892/you-dont-have-write-permissions-for-the-var-lib-gems-2-3-0-directory

- Install Jekyll:
  ```
  gem install bundler jekyll
  ```
- Create a Jekyll Site:
  ```
  jekyll new your-site-name
  ```
- Change Directory
   ```
   cd your-site-name
   ```
- Run Jekyll Locally
   ```
   bundle exec jekyll serve
   ```

1. Markdown and Liquid Templates: You write your content in Markdown, a lightweight markup language. You can also use Liquid, a templating language, to add dynamic elements to your pages.
2. Configuration: You define the site's configuration in a `_config.yml` file. This includes settings like the site title, author, and plugins.
3. Content: Your content, written in Markdown, is placed in the `_posts` or other designated directories.
4. Layouts and Templates: Jekyll uses layouts and templates to structure your site. You can create custom layouts or use the default ones provided by Jekyll.
5. Conversion: Jekyll takes your Markdown files, processes them using Liquid, and converts them into HTML pages.
6. Plugins: Jekyll supports plugins that add functionality to your site, such as SEO optimization, social media integration, or sitemaps.
7. Building: To generate the site, you run the `jekyll build` command. This processes your content, applies templates, and creates an output directory with HTML files.
8. Output: The generated HTML files, along with other assets like CSS and JavaScript, are ready to be deployed to a web server.
9. Deployment: You can deploy the static site to any web server or hosting service, as it's just a collection of static files.

- ![[what i expect from exposés on technologies#^anchor-tech-internals]]
- ![[what i expect from exposés on technologies#^anchor-production-problems]]
