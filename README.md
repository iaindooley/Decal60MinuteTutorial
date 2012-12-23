# Before starting:

## What is Decal CMS?

Decal CMS is a hosted content management system that aims to make it simple and cost effective to deploy editable sites with highly structured markup.

We want to make Decal a system you can use for all sites, large or small, and even as a "cloud CMS" to plug in content management to highly complex web applications (via the API).

We also want to ensure that our system for extending Decal with custom functionality is the most flexible and simple to use of any CMS, even though it is a hosted product.

## This should take you about 60 minutes

Thanks for taking an interested in Decal CMS. The following tutorial is designed to give you a more in-depth introduction to Decal CMS following on from your initial interest in our "Whirlwind Tour" at http://www.decalcms.com/tour/

## What is the purpose of this tutorial?

Decal does a lot of things right and we use it in production for our own clients.

There are a number of things we need to do before other web developers can use it and the purpose of this tutorial is to find out if we're on the right track.

We'd like to build enough support to launch a Kickstarter campaign so we can fix these major flaws and launch Decal CMS for public use.

So please bear this in mind as you take the tutorial and when you're done, please email team@workingsoftware.com.au and tell us whether you'd back us or not!

## List of the biggest things that we want to fix:

Here is a list of the biggest issues we're aware of that we'd like to fix prior to launching this product for public use. Please take a moment to review them and bear these in mind when taking this tutorial:

 - Deployment via ZIP only
 - Editing interface works in Firefox only
 - Image and embed placement is problematic
 - Caveats with what markup can be made editable
 - Doctype is always HTML5 style
 - Cumbersome file manager
 - Project and interface CSS can interfere with each other
 - Serious lack of documentation and vague, ambiguous or non-existent error reporting
 - API design issues
 - We need hosting on all major continents
 - Using data-dcl prefixes on decal attributes

More details on each of these points is included as an appendix at the end of the tutorial in the section "Detailed description of issues we aim to fix before launching for public use".

We thought it prudent to present this list at the beginning of the tutorial but didn't want to get too bogged down in it!

# Tutorial

## How this tutorial is structured

Each section deals with a specific feature of Decal. We start with the most simple, and progress to more complex features as we go through.

The goal for Decal is to allow you to deploy and edit completely arbitrary HTML, but the current version has some limitations. We plan on fixing those if we get enough support for the project.

For the sake of simplicity in this tutorial, we have created a sample HTML project for you to deploy, but we encourage you to play around with deploying a project of your own afterwards and let us know what problems you encounter.

## Some instructional videos

The following link will take you to some instructional videos on our website:

http://www.decalcms.com/page/Support#instructionalVideos

They are aimed at *users* and show you how the editing interface works. They're a little outdated, but it would be a good idea to watch them now. There is about 15 minutes of video content in total and watching it now will give you a bit of context for the rest of the tutorial.

## Step 1: Hello World (the simplest possible site)

Create a folder called "MyProject" and in it, create a file called home.html and paste the following HTML into it:

    <html>
        <head>
            <title>Ohai</title>
        </head>
        <body>
            <div area="Main content" editable="true" id="mainContent">
                <h1>Sample content is instructional</h1>
                <h2>This is what the user sees when they create a new page</h2>
                <p>You can also include images if you like:</p>
                <p><img src="http://dummy.mockups.decalcms.com/200x200" /></p>
            </div>
        </body>
    </html>

Now create a ZIP archive from the folder called MyProject.zip.

Go to:

http://manager.decalcms.com/

and sign-up for a new account.

*NB: If you're in the United States you should go to http://manager.us.decalcms.com/ to use our US server which will be faster*

In the top menu bar click "Add Site" and name it "My Project" then select the MyProject.zip file you created and upload it.

Once the site has finished preparing, you can click "Launch" to launch the editor for the site. If you follow the on-screen prompts to create a page, you'll see that you can edit the content in the div.

After you've had a play around with the interface, you can deactivate the site.

## Step 2: Adding some structure, tags and formatting

Repeat the same process you went through in Step 1 using the following HTML:

    <html>
        <head>
            <title>Ohai</title>
        </head>
        <body>
            <div area="Main content" id="whatever">
                <h1 editable="true" tags="none">This is where you type your content</h1>
                <p editable="true" tags="inline">This allows inline formatting only</p>
            </div>
        </body>
    </html>

Unlike the first step, you're now much more limited in terms of what formatting you're able to apply.

## Step 3: Repeatable vs. fixed components and containers

Now repeat the same process again, using the following HTML:

    <html>
        <head>
            <title>Ohai</title>
        </head>
        <body>
            <div area="Main content">
                <div component="Title content" id="whatever">
                    <h1 editable="true">This is a fixed component because it has an id attribute</h1>
                    <p editable="true" tags="inline">The user does not need to choose to add a main content area.</p>
                    <p editable="true" tags="inline">If the user clicks the green arrow at the top right, and chooses to add a component after, they can add another div.</p>
                </div>
                <div component="Title content">
                    <h1 editable="true">This component is repeatable because the containing div does not have an id attribute</h1>
                    <p editable="true" tags="inline">It can be structured however you like</p>
                    <br />
                    <img editable="true" width="200" src="http://dummy.mockups.decalcms.com/200x200/" />
                    <div editable="true">
                        <h3>The user can use any kind of formatting here</h3>
                    </div>
                    <div editable="true" tags="embed">
                        <p>Click here to embed some snippet of code (eg. a Wufoo form or YouTube video)</p>
                    </div>
                </div>
            </div>
            <div area="Sub content">
                <div component="Sub content intro" id="something">
                    <h2>This area allows more than one type of component</h2>
                    <p>This first component is fixed, but unlike the previous area, if you click the green arrow at the top right, you'll be given the option to add one or more components.</p>
                    <p>As you mouse over each in the menu, you will see the sample content appear in the document.</p>
                </div>
                <div component="Component type 1">
                    <h2 editable="true" tags="none">This component has a heading</h2>
                    <p editable="true" tags="inline">And some body text</p>
                    <br />
                    <img editable="true" width="200" src="http://dummy.mockups.decalcms.com/200x200/" />
                    <br />
                    <a editable="true" href="">This link is editable (but the text isn't)</a>
                    <p>You can include non-editable markup in a component, too</p>
                </div>
                <div component="Component type 2">
                    <h3 editable="true" tags="none">This component has a different heading and an image</h3>
                    <br />
                    <img editable="true" width="200" src="http://dummy.mockups.decalcms.com/200x200/" />
                </div>
            </div>
        </body>
    </html>

Now repeat the process again to deploy this as a new site.

Have a play with the interface, add in and edit a few components, then go back to the source code and note how the following attributes have been added to create that highly structured interface:

 - area: defines an editable area
 - component: defines a component (some HTML structure) allowed within that area. If used in conjunction with an id attribute will create a "fixed" component that always exists on the page
 - editable: denotes a node which can be edited. Currently this can only applied to h1-6, p, div and li nodes.
 - tags: used in conjunction with an editable attribute to indicate what formatting should be allowed. Use a comma separated list of allowed formats, or the shorthand "none" to disallow all formatting or "inline" to allow inline styles only. The complete list is h1-6,p,br,ol,ul,li,img,embed,em,u,strong,a.

## Step 4: Custom classes and link styles

In this step, we'll add a stylesheet to the project and use the "Update" button to update an existing site in the manager interface, rather than using the "add site" button.

Firstly, create a file called styles.css in your project folder and put the following CSS code in it:

    p.specialParagraph /* decal: Red text */
    {
        color:red;
        background:blue;
    }
    
    p.anotherType /* decal: Ugly paragraph */
    {
        border:1px solid red;
        background:black;
        text:white;
    }
    
    a.linkTypeOne /* Red link text */
    {
        color:red;
    }
    
    a.linkTypeTwo /* Green link text */
    {
        color:green;
    }

Now update your home.html file with the following code - note that it's identical save for the inclusion of the styles.css file above:

    <html>
        <head>
            <title>Ohai</title>
            <link rel="stylesheet" type="text/css" href="styles.css" />
        </head>
        <body>
            <div area="Main content">
                <div component="Title content" id="whatever">
                    <h1 editable="true">This is a fixed component because it has an id attribute</h1>
                    <p editable="true" tags="inline">The user does not need to choose to add a main content area.</p>
                    <p editable="true" tags="inline">If the user clicks the green arrow at the top right, and chooses to add a component after, they can add another div.</p>
                </div>
                <div component="Title content">
                    <h1 editable="true">This component is repeatable because the containing div does not have an id attribute</h1>
                    <p editable="true" tags="inline">It can be structured however you like</p>
                    <br />
                    <img editable="true" width="200" src="http://dummy.mockups.decalcms.com/200x200/" />
                    <div editable="true">
                        <h3>The user can use any kind of formatting here</h3>
                    </div>
                    <div editable="true" tags="embed">
                        <p>Click here to embed some snippet of code (eg. a Wufoo form or YouTube video)</p>
                    </div>
                </div>
            </div>
            <div area="Sub content">
                <div component="Sub content intro" id="something">
                    <h2>This area allows more than one type of component</h2>
                    <p>This first component is fixed, but unlike the previous area, if you click the green arrow at the top right, you'll be given the option to add one or more components.</p>
                    <p>As you mouse over each in the menu, you will see the sample content appear in the document.</p>
                </div>
                <div component="Component type 1">
                    <h2 editable="true" tags="none">This component has a heading</h2>
                    <p editable="true" tags="inline">And some body text</p>
                    <br />
                    <img editable="true" width="200" src="http://dummy.mockups.decalcms.com/200x200/" />
                    <br />
                    <a editable="true" href="">This link is editable (but the text isn't)</a>
                    <p>You can include non-editable markup in a component, too</p>
                </div>
                <div component="Component type 2">
                    <h3 editable="true" tags="none">This component has a different heading and an image</h3>
                    <br />
                    <img editable="true" width="200" src="http://dummy.mockups.decalcms.com/200x200/" />
                </div>
            </div>
        </body>
    </html>

Now go back into edit your site. You will need to reload the page or at least lock/unlock the page you were working on in order to grab the new markup and stylesheet).

You will now see that whenever you edit a link, you'll have the link styles available that are included in the CSS, and in the style menu in the toolbar you'll have the style options defined for "Red Text" and "Ugly Paragraph" whenever you click onto a paragraph node.

The way this works is that you can define these custom styles and whenever you click onto a block node which matches the selector used for the style, the user will have the option to choose one of these custom styles from the menu in order to apply that class.

Currently you can *only* apply these to editable block level elements (ie. h1-6, p, div and li nodes) however our goal is to expand why types of elements you can target with custom CSS styles (for example allowing you to create an editable span tag and letting the user choose one of several available styles to apply to it).

## Step 5: Images, embeds and the file manager

The tutorial videos at the beginning included one on using files and video embeds.

The following code has a mixture of an openly editable div, an area which contains only an editable image and an area which contains a div capable only of having an object embedded (using the tags="embed" attribute).

The sample content in the following HTML describes how each area will operate. Copy and paste this into a file called images_embeds.html in your project and then re-zip it:

    <html>
        <head>
            <title>My page</title>
        </head>
        <body>
            <div area="Main content" id="mainContent" editable="true">
                <h2>You can use any formatting here, including images and embeds</h2>
                <p>If you put in a bunch of content in here, then embed an image just like in the instructional video you'll see you can move it around.</p>
                <p>You can do the same thing with embeds.</p>
                <p>The one thing you should notice is that the dropping and placement of images is a bit cumbersome. Although you can drag images around and position them when you release the mouse it's not always ending up in the correct spot.</p>
                <p>This is because, unlike other WYSIWYG editors, Decal doesn't use hard coded inline styles to allow you to place images wherever you like. This is technically better, but makes for a lousy user experience when editing the page.</p>
            </div>
            <div area="Image content" id="imageContent">
                <h2>If you create a more structured format</h2>
                <p>You can use editable images to make the user experience much simpler, and the design of the site much more difficult to break.</p>
                <p><img editable="true" width="400" src="http://dummy.mockups.decalcms.com/400x200?text=Right+click" /></p>
            </div>
            <div area="Video content" id="videoContent">
                <h2>You can use the tags="embed" attribute to create an area that will prompt someone to embed a snippet (eg. video or form)</h2>
                <p>This makes the task of getting someone to embed a video much simpler than expecting them to embed an object in an openly editable area</p>
                <div editable="true" tags="embed">Click here to embed a video</div>
            </div>
        </body>
    </html>

When you upload it you can use the "Update" button instead of adding a new site. When you click "add page" now you will see the template called "Images Embeds". Add a page using this template and have a play around with embedding images and other objects in the openly editable area and see how the experience compares with using the editable image and the editable div that allows only embeds via the tags attribute.

## Step 6: Area scoping

For this step, create a new folder called "My Second Project" and inside, create a file called home.html and paste the following code into it:

    <html>
        <head>
            <title>My Page</title>
        </head>
        <body>
            <div area="Main content" editable="true">
                <h2>This is the home page</h2>
                <p>You can type a bunch of content here, and it will only update on one page.</p>
            </div>
            <div area="Sub content" editable="true" scope="superglobal">
                <h2>This is a superglobal area</h2>
                <p>You can update the content here and any page that uses a template containing an area with the same name will receive the updates</p>
            </div>
        </body>
    </html>

Now create a file called about.html and paste the following code into it:

    <html>
        <head>
            <title>My Page</title>
        </head>
        <body>
            <div area="Main content" editable="true">
                <h2>This is the about page</h2>
                <p>You can type a bunch of content here and it will only update on one page.</p>
            </div>
            <div area="Sub content" editable="true" scope="superglobal">
                <h2>This is a superglobal area</h2>
                <p>Anything you type here will appear on any other page using a template which contains this area.</p>
            </div>
            <div area="Related content" editable="true" scope="global">
                <h2>This is a global area</h2>
                <p>Anything you type here will appear on any other page using the About page template</p>
            </div>
        </body>
    </html>

Notice how in each template, we've included optional "scope" attributes on some of the areas, to call these areas either global or superglobal.

Create a ZIP file from this new folder and upload it using the "Add Site" button in the Decal Manager interface, calling the site "Tutorial Step 6".

If you go in and add 2 pages using the About template, and one page using the Home template, then note how when you change content in an area scoped "global" on a page using the About template, it updates on both pages at once (you can switch between them to see how). If you update content in the area marked "superglobal", then it updates on all pages which contain an area with the same name, ie. the same content now appears on both pages using the About template, as well as the page created using the Home template.

## Step 7: Menus and the menu manager

The video tutorials linked at the start of this tutorial showed you the basics of how to use the menu manager to add and edit menu items.

To implement menus in your templates, you can create a nested menu structure using arbitrary HTML on your page using the menu attribute, and a couple of related attributes.

For starters, create a new folder called "My Menu Project" and create a file in it called home.html then paste the following code into it:

    <html>
        <head>
            <title>My Page</title>
        </head>
        <body>
            <div id="mainNavigation" menu="Main Navigation">
                <div repeat="10" active-class="main-highlight">
                    <p><a href="" characters="20">This is an item</a></p>
                    <div repeat="10" active-class="main-sub-highlight">
                        <p><a href="" characters="60">This is a sub menu item</a></p>
                    </div>
                    <div>
                        <p><a href="">This is a sub menu item</a></p>
                    </div>
                    <div>
                        <p><a href="">This is a sub menu item</a></p>
                    </div>
                    <div>
                        <p><a href="">This is a sub menu item</a></p>
                    </div>
                    <div>
                        <p><a href="">This is a sub menu item</a></p>
                    </div>
                </div>
                <div>
                    <p><a href="">This is an item</a></p>
                    <div>
                        <p><a href="">This is a sub menu item</a></p>
                    </div>
                </div>
                <div>
                    <p><a href="">This is an item</a></p>
                    <div>
                        <p><a href="">This is a sub menu item</a></p>
                    </div>
                </div>
                <div>
                    <p><a href="">This is an item</a></p>
                    <div>
                        <p><a href="">This is a sub menu item</a></p>
                    </div>
                </div>
            </div>
            <div area="Main content" editable="true">
                <h2>This is the about page</h2>
                <p>You can type a bunch of content here and it will only update on one page.</p>
            </div>
            <div area="Sub content" editable="true" scope="superglobal">
                <h2>This is a superglobal area</h2>
                <p>Anything you type here will appear on any other page using a template which contains this area.</p>
            </div>
            <div area="Related content" editable="true" scope="global">
                <h2>This is a global area</h2>
                <p>Anything you type here will appear on any other page using the About page template</p>
            </div>
            <ul id="footerNavigation" menu="Footer Navigation">
                <li repeat="6" active-class="footer-menu-highlight" ancestor-class="footer-menu-parent-highlight">
                    <a href="" characters="20">This is a menu item</a>
                    <ul submenu="Footer sub menu">
                        <li repeat="10" active-class="footer-sub-menu-highlight">
                            <a href="" characters="60">This is a sub menu item</a>
                        </li>
                    </ul>
                <li>
                <li>
                    <a href="">This is a menu item</a>
                    <ul>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                    </ul>
                <li>
                <li>
                    <a href="">This is a menu item</a>
                    <ul>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                    </ul>
                <li>
                <li>
                    <a href="">This is a menu item</a>
                    <ul>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                    </ul>
                <li>
                <li>
                    <a href="">This is a menu item</a>
                    <ul>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                        <li>
                            <a href="">This is a sub menu item</a>
                        </li>
                    </ul>
                <li>
            </ul>
        </body>
    </html>

You can now create a ZIP file from this folder and upload it using the "Add Site" button, naming the site something like "My Menu Project".

If you add a page now, using the Home template and call it "Home Page", then click back to the site manager tab and go to manage one of your menus, you can add a link to this Home page in the menu as per the instructional video at the start of this tutorial.

### Detailed notes about how menus work:

 - Menu content is managed via the Menu Manager rather than directly on the page like other content (this is something we want to change in future)
 - The "menu" attribute indicates a "top level" menu
 - The "submenu" attribute indicates a sub menu
 - Any node with a "repeat" attribute will become an available "slot" in the menu manager. The repeat attribute ensures that the user is unable to add more than the specified number of items (since this will often break the design of the site). You can have sample content in the page during development. When you deploy the site, Decal will automatically remove any sibling nodes of a node with a repeat attribute. Note that you only need to add the attributes to one of your menu items, the rest are just filler so you can see how the page will look when viewing the HTML statically.
 - The active-class and ancestor-class activate when a node contains an anchor node with an href attribute the same as the URL currently being viewed
 - The characters attribute goes on the node which will have the link set to whatever the user enters via the menu manager. The number of characters indicates the maximum allowed characters during editing. This allows you to prevent someone from breaking the design during editing
 - When a page is set to have Private access, the menu item node which contains a link to that page will be hidden from the site except when someone is logged in (useful for creating a menu item with special administrative functions or linking to instructions for using the CMS
 - Menus are superglobal. The content will update on all pages when it is edited, however you don't necessarily have to use the same menus on all pages (ie. you can have templates with differently named menus that are managed separately)
 
## Step 8: Filters

The architecture for creating "plugins" or extensions for Decal CMS is called "Filters".

The concept is very simple but very different from all other content management systems (both hosted and self-hosted).

Decal Filters use a Service Oriented Architecture, meaning that they can be written in any language, and hosted anywhere.

As a simple example, we're going to create a filter which provides a sidebar navigation of recently created pages using the current template, and a list of "related pages" that are tagged the same as the current page. This could be used, for example, to provide a list of "recent posts" on a blog, as well as a list of articles the reader "may also like".

Firstly, create a new project called "My Blog" and in it create a file called blog_entry.html and paste the following code into it:

    <html>
        <head>
            <title>This is a page</title>
        </head>
        <body>
            <h2 area="Post title" editable="true" tags="none">This is the title of the post</h2>
            <div area="Body content" editable="true">
                <p>Type the content of your post here</p>
            </div>
            <ul id="recommendedPosts">
                <li id="header">If you liked this post, you might also like ... </li>
                <li>A list of related</li>
                <li>Posts will appear here</li>
                <li>Automatically</li>
            </ul>
            <ul id="recentPosts">
                <li>This will</li>
                <li>Be a list of recent</li>
                <li>posts that will populate</li>
                <li>automatically</li>
            </ul>
        </body>
    </html>

Create a ZIP file of the project called MyBlog.zip and use the Add Site button in the Decal Manager to create a new site, called "My Blog".

Now launch the content editor and create a few pages. When creating the pages, tag them so that the first and second post two share at least one tag, and the second and third post share at least one tag, for example:

 - Post 1 tagged with "one,two"
 - Post 2 tagged with "two,three"
 - Post 3 tagged with "three,four"

To setup a filter, first you need to setup somewhere to run/host the code.

TODO: INSTRUCTIONS FOR DOING THIS ON HEROKU OR APPFOG FREE TIER WITH PYTHON, RUBY AND PHP AS PASSTHROUGH, EG. die($_POST['data']);

Now that you have a URL to do the filtering, you simply add it to the head of your document. In your "My Blog" folder, replace the blog_entry.html template with the following code. Note that the only difference is the presence of a "filter" node in the head of the document:

    <html>
        <head>
            <title>This is a page</title>
            <filter url="http://YOUR.URL.COM/" />
        </head>
        <body>
            <h2 area="Post title" editable="true" tags="none">This is the title of the post</h2>
            <div area="Body content" editable="true">
                <p>Type the content of your post here</p>
            </div>
            <ul id="recommendedPosts">
                <li id="header">If you liked this post, you might also like ... </li>
                <li>A list of related</li>
                <li>Posts will appear here</li>
                <li>Automatically</li>
            </ul>
            <ul id="recentPosts">
                <li>This will</li>
                <li>Be a list of recent</li>
                <li>posts that will populate</li>
                <li>automatically</li>
            </ul>
        </body>
    </html>

Now when you load the page, the code at that URL will be executed. The first thing to do is make it not execute when you're logged in and editing the page (which makes the page load more quickly).

TODO: INSTRUCTIONS FOR DOING THIS IN PHP, RUBY, PYTHON

You can now write code to populate the the list of recent and recommended posts.

TODO :INSTRUCTIONS FOR DOING THIS IN PHP, RUBY, PYTHON USING THE API

The responses are all cached, which can be enabled/disabled in the Decal Manager. You can also enable/disable app widgets in the Decal Manager to prevent them from being loaded.

# Detailed description of issues we aim to fix before launching for public use

## Deployment via ZIP only

This means that every time you make a change you have to re-upload the entire project as a ZIP file which can be very time consuming, slowing down the speed at which you can iterate.

## Editing interface in Firefox only

Obviously sites built with Decal work in any browser, but the editing and backend interfaces used to manage the content currently only work in Firefox. The Decal tour at http://www.decalcms.com/tour/ uses a modified version of the editor which works in Chrome, Safari and Firefox so we aim to port those changes back into the main codebase.

## Image and embed placement is problematic

Unlike other in-browser rich text editors, Decal won't add any inline styles to position images. Although the positioning works well it can be unintuitive.

## Caveats with what markup can be made editable

Currently only div, p and li nodes can be made editable and in-line formatting is limited to em, strong and u. We want to add support for editing a greater range of nodes, including HTML5 element types and inline nodes (eg. spans)

## Doctype is always HTML5 style

Currently you can't set the doctype from your templates, it's hard coded into the Decal CMS output as <!DOCTYPE html>

## Cumbersome file manager

The process of adding and managing files and images to the site is quite long winded. Ideally we want to integrate directly with Dropbox or other cloud storage solutions to simplify the process of placing media on your site.

## Project and interface CSS can interfere with each other

Because Decal CMS allows you to edit content right on the page, we've found that sometimes the CSS you use to style your page, can impact on how the Decal CMS interface renders. We need to restructure the CSS in Decal to ensure it never conflicts with the CSS in your project.

## Serious lack of documentation and vague, ambiguous or non-existent error reporting

Currently it's very easy to get confused, stuck or otherwise completely immobilised while deploying a Decal project. Whilst a lot of this can be solved with better documentation, we also need to make sure that any and all errors are accurately reported with helpful error messages and making things much more robust.

## API design issues

Our API currently isn't particularly intuitive to use. It works, and it's good, but the naming of the parameters and the formatting of the reqeusts needs work.

## Hosting on all major continents

Currently we only have hosting in one location in the US, and in Australia. We want to expand to ensure we're present on all major continents.

## Using data-dcl prefixes on decal attributes

When you deploy with Decal CMS, you use attributes on your HTML. Currently these attributes aren't easily distinguishable from other HTML attributes.
