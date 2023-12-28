# Table of content
[Docsify](#Docsify)  
[Key Features of Docsify](#key-features-of-docsify)  
[Step by step guide to installation and Setup](#step-by-step-guide-to-installation-and-setup)  
[Customization](#customization)  
[Themes](#themes)  
[List of Plugins](#list-of-plugins)  
[Markdown Uses](#markdown-uses)  
[Deploy](#deploy)


# Docsify
> Docsify is a lightweight, flexible, and easy-to-use documentation generator designed for creating clean and elegant documentation websites. It simplifies the process of building and maintaining documentation, providing a dynamic and fast browsing experience for users. Docsify operates as a single-page application (SPA), meaning that it dynamically loads content on the client side, resulting in quick navigation without page reloads.

# Key Features of Docsify
### Markdown Support
Docsify primarily uses Markdown for writing documentation, allowing developers to focus on content creation without dealing with complex markup.
### Dynamic Loading
Content is loaded dynamically on the client side, providing a smooth and seamless browsing experience. This approach improves performance by avoiding full-page reloads.
### Single Page Application (SPA)
Docsify operates as a single-page application, loading all necessary resources initially and updating content dynamically as users navigate through the documentation.
### External Link Target:
Customize the behavior of external links, specifying whether they should open in the same tab or a new tab.
### Navigation Sidebar
Automatically generates a navigation sidebar based on the structure of the documentation, making it easy for users to navigate through different sections.
### Search Functionality
Provides a built-in search feature that allows users to quickly find relevant information within the documentation.
### Theming and Customization
Highly customizable, allowing users to change the appearance and behavior of their documentation site by using custom themes and plugins.
### GitHub Integration
Easily integrates with GitHub repositories, enabling users to host their documentation directly from GitHub Pages.
### Easy Installation and Setup
Simple installation process using npm, and an initialization command that sets up the necessary files and directories.
### Cross-Platform Compatibility
Works well on different platforms, providing a consistent documentation experience for users regardless of their operating system.

# Step by step guide to installation and Setup
## Prerequisite

* Node 
* Npm 
* Gitpages
* Docker
To check the system configuration run the following command:
```
cat /etc/os-release
```
Output:  
PRETTY_NAME="Ubuntu 22.04.3 LTS"  
NAME="Ubuntu"   
VERSION_ID="22.04"  
VERSION="22.04.3 LTS (Jammy Jellyfish)"  
VERSION_CODENAME=jammy  
ID=ubuntu  
ID_LIKE=debian  
HOME_URL="https://www.ubuntu.com/"  
SUPPORT_URL="https://help.ubuntu.com/"  
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"  
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"  
UBUNTU_CODENAME=jammy  

To ensure that your system is aware of the latest information about available software packages, versions, and dependencies run the following commands
```
sudo apt update
sudo apt upgrade
```
### Step 1: Install Node.js
Docsify requires Node.js and npm (Node Package Manager) to be installed on your system. You can install them using the following commands:

To install nodejs
```
sudo apt install nodejs
```
To check the version,run the following command:
```
node --version
```
Output:  
```
v12.22.9
```
### Step 2: Install npm
To install the npm, use the following command:
```
sudo apt install npm
```
To check the version,run the following command:
```
npm --version
```
Output:
```
8.5.1
```
### Step:3 To install docsify
```
sudo npm install -g docsify-cli
```
Output:  

/usr/bin/docsify -> /usr/lib/node_modules/docsify-cli/bin/docsify

> docsify@4.13.1 postinstall /usr/lib/node_modules/docsify-cli/node_modules/docsify
> opencollective-postinstall

Thank you for using docsify!
If you rely on this package, please consider supporting our open collective:
> https://opencollective.com/docsify/donate

+ docsify-cli@4.4.4
added 204 packages from 94 contributors in 23.743s

To check the version,run the following command:
```
docsify --version
```
Output
```
docsify -cli version:
4.4.4
```
Create a directory to run the docsify
To create directory run the following command:
```
mkdir docsify
```
Now change the directory to docsify
```
cd docsify
```
Output
```
brijesh@brijesh-Aspire-Lite-AL15-51:~/docsify$ 
```
Initialize the docsify in newly created directory:
```
docsify init .
```
Output:
```
Initialization succeeded! Please run docsify serve
```
After the init is complete,you can see the file in the ./docsify subdirectory
* index.html as the entry file  
* README.md as the home page  

To run the docsify run the following command:
```
docsify serve
```
Output:
```
Serving /home/brijesh/docsify now.
Listening at http://localhost:3000
```
You can preview your site in your browser on http://localhost:3000.

### To add more pages
If you need more pages, you can simply create more markdown files in your docsify directory.  
Example:
In the docsify directory create a file named intro.md:
```
touch introduction.md
```
touch command is used to create a new empty file.

You can edit the introduction.md file by the following command  
```
vim introduction.md
```
Vim is a text editor which is used for editing.

# Customization
Docsify provides various configuration options to customize the appearance and behavior of your documentation. These options are typically set in the index.js file in the docsify directory. Below are some of the commonly used configuration options:
## Sidebar
In Docsify, the sidebar is a navigational menu displayed on the side of your documentation site. It provides links to different sections or pages of your documentation. The sidebar is typically defined in a "_sidebar.md" file in your project.
* Create a "_sidebar.md" file in your docsify directory.
* Add the content of sidebar in Markdown format  
Example
```
* [Home](/)
* [Introduction](/introduction.md)
* [Installation](/installation.md)
* [Configuration](/configuration.md)
```
The format is [Link Text]("relative path to your file.md").
To see the customized sidebar you need to set the loadsidebar to true in your index.html file.
```
<script>
  window.$docsify = {
    loadSidebar: true
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```
<b>You need to create a .nojekyll in ./docsify to prevent GitHub Pages from ignoring files that begin with an underscore.</b>

## Set Page Titles from Sidebar Selection
You can customize the title by specifying a string after the filename in "_sidebar.md"  
Example:  
```
<!-- docsify/_sidebar.md -->
* [Home](/)
* [Introduction](guide.md "Who I am")
``` 
## Table of Contents
Table of contents is automatically generated once you have created the "_sidebar.md" but you can customize the table of contents by setting "subMaxLevel".
```<script>
  window.$docsify = {
    loadSidebar: true,
    subMaxLevel: 2
}
</script>
```
## Ignoring Subheaders
If you want to ignore any subheader you can do so by adding <!-- {docsify-ignore} ---> to the subheader
```
# Getting Started

## Header <!-- {docsify-ignore} -->
```

This header won't appear in the sidebar table of contents.
## Custom Navbar
You can create a custom markdown-based navigation file by setting loadNavbar to true and creating "_navbar.md" in your docsify directory
To create the "_navbar.md":
```
cd docsify
touch _navbar.md
```
Edit the _navbar.md as per your requirement For example
```
<!-- _navbar.md -->

* [Hindi](/)
* [English](/En/)
```
To see the changes edit your html file to loadNavbar:true
```
<!-- index.html -->

<script>
  window.$docsify = {
    loadNavbar: true
  }
</script>
```
## Nested Navbar
You can also create a nested navbar by nesting the sub-element under a parent element
```
<!-- _navbar.md -->

* Getting started

  * [Quick start](quickstart.md)
  * [Writing more pages](more-pages.md)
* Configuration
  * [Configuration](configuration.md)
  * [Themes](themes.md)
```
## Cover Page
You can create  a cover page by setting the coverpage to true and creating a "_coverpage.md" file in your docsify directory.
```
<!-- index.html -->

<script>
  window.$docsify = {
    coverpage: true
  }
</script>
```
```
<!-- _coverpage.md -->

![logo](_media/icon.svg)

# docsify <small>3.5</small>

> A magical documentation site generator.

- Simple and lightweight
- No statically built html files
- Multiple themes
```
You can also customize the background colour or background image:
```
<!-- _coverpage.md -->
# docsify <small>3.5</small>

<!-- background image -->

![](_media/bg.png)

<!-- background color -->

![color](#f0f0f0)
```
## auto2top
By setting this option to true, you can automatically go to the top of the page when you change the route
```
window.$docsify = {
  auto2top: true,
};
```
## externalLinkTarget
externalLinkTarget is a property used to specify the target for opening external links within the rendered markdown content. The default value is "_blank", which means external links will open in a new tab.
```
window.$docsify = {
  externalLinkTarget: '_blank', // default
};

```
If you want to open the external link into the same tab then you can set the externalLink to "_self"
```
window.$docsify = {
  externalLinkTarget: '_self',
};
```
## hideSidebar
You can hide your sidebar.This will hide your sidebar and will not render anything on your sidebar.
```
window.$docsify = {
  hideSidebar: true,
};
```
## logo
You can set the logo of your website.It appears in the sidebar.
```
window.$docsify = {
  logo: '/_media/icon.svg',
};
```
## maxLevel
This is used to show the contents of the table you can set the maxLevel to decide which headings will be shown in table of contents
```
window.$docsify = {
  maxLevel: 4,
};
```
## mergeNavbar
You can merge the navigation bar for the smaller screens
```
window.$docsify = {
  mergeNavbar: true,
};
```
## name
You can give a name to your website as it appears into the sidebar:
```
window.$docsify = {
  name: 'docsify',
};
```
## nativeEmoji
You can also use emoji in your contents.To use the emoji turn on the nativeEmoji to true in index.html and use the emoji as per given exampel.
```
window.$docsify = {
  nativeEmoji: true,
};
```
Example:
```
:smile: 
:partying_face:
:joy:
:+1:
:-1:
```
## repo
By this option you can add your github account to the top right corner of your page.
```
window.$docsify = {
  repo: 'https://github.com/docsifyjs/docsify/',
};
```
## themeColor
Customize the theme color of your Docsify documentation site. It uses the CSS3 variables feature to define a color variable, and this variable is then used in the styling of various elements.
```
window.$docsify = {
  themeColor: '#3F51B5',
};
```

# Themes
There are a handful of official and community made themes which you can use to give your pages a nice look.
```
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/vue.css" />
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/buble.css" />
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/dark.css" />
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/pure.css" />
```
# List of Plugins
In Docsify, plugins are additional JavaScript modules or extensions that extend the functionality of the documentation site. Plugins can be used to add new features, customize behavior, or integrate third-party tools seamlessly into Docsify.
## Zoom Image
You can enable the zoom option by using the following plugin.
```
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/zoom-image.min.js"></script>
```
## Copy to Clipboard
Add a simple "Click to copy" button to all preformatted code blocks to effortlessly allow users to copy example code from your document.
```
<script src="//cdn.jsdelivr.net/npm/docsify-copy-code/dist/docsify-copy-code.min.js"></script>
```
## Full Text Search
You can enable the search option by using the full text search option.It helps you in searching any word in the document.
```
<script>
  window.$docsify = {
    search: 'auto', // default

    search: [
      '/',            // => /README.md
      '/guide',       // => /guide.md
      '/get-started', // => /get-started.md
      '/zh-cn/',      // => /zh-cn/README.md
    ],

    // complete configuration parameters
    search: {
      maxAge: 86400000, // Expiration time, the default one day
      paths: [], // or 'auto'
      placeholder: 'Type to search',

      // Localization
      placeholder: {
        '/zh-cn/': 'Eng',
        '/': 'Type to search',
      },

      noData: 'No Results!',

      // Localization
      noData: {
        '/zh-cn/': 'Eng',
        '/': 'No Results',
      },

      // Headline depth, 1 - 6
      depth: 2,

      hideOtherSidebarContent: false, // whether or not to hide other sidebar content

      // To avoid search index collision
      // between multiple websites under the same domain
      namespace: 'website-1',

      // Use different indexes for path prefixes (namespaces).
      // NOTE: Only works in 'auto' mode.
      //
      // When initializing an index, we look for the first path from the sidebar.
      // If it matches the prefix from the list, we switch to the corresponding index.
      pathNamespaces: ['/zh-cn', '/ru-ru', '/ru-ru/v1'],

      // You can provide a regexp to match prefixes. In this case,
      // the matching substring will be used to identify the index
      pathNamespaces: /^(\/(zh-cn|ru-ru))?(\/(v1|v2))?/,
    },
  };
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
```
# Markdown Uses
Markdown plays a crucial role in Docsify.Docsify relies on Markdown files to create dynamic and user-friendly documentation websites. Here are some of the key uses of Markdown in Docsify
* Markdown Files: Docsify documentation is typically written using Markdown files. Markdown provides a lightweight and easy-to-write syntax for creating formatted text without the need for HTML.
Structured Documentation:

* Headings: Markdown headings (#, ##, ###, etc.) are used to structure the documentation. These headings define sections and subsections, creating a clear hierarchy.  

* Text Formatting:
Markdown allows authors to easily apply formatting to text. For example, **bold** and *italic* are used for bold and italic text, respectively.

* Hyperlinks: Authors can create hyperlinks with ease using the [text](/url/ ':disabled') syntax.

* Code Examples: Markdown supports code blocks using backticks (```). This is essential for displaying code snippets in documentation.
* Extensible with HTML:
HTML Integration: Markdown files in Docsify can include HTML code directly, providing flexibility for more complex layout and styling requirements.
# Deploy
Deploying a Docsify documentation site involves hosting the generated HTML files on a web server or a platform that supports static site hosting.
## Githubpages
### Step 1: Create a repository
To deploy your docsify document on your githubpages follow these steps:
* Go to your GitHub account.

* Click on the "+" sign in the top right corner and select "New repository."

* Enter a repository name, provide a description, and initialize the repository with a README.md if desired.

* Click "Create repository."
### Step 2: Clone the Repository to Your Local Machine
Use the following command to clone the repository to your local machine
```
git clone https://github.com/your-username/your-repository.git
cd your-repository

```
### Step 3: Commit and Push Changes
```
cd ..  # Move back to the root of the repository
git add .
git commit -m "Initial documentation"
git push origin master

```
### Step 4: Configure GitHub Pages
* Go to your GitHub repository.

* Click on "Settings."

* Scroll down to the "GitHub Pages" section.

* Set the "Source" branch to master (or the branch where your Docsify documentation resides).

* Click "Save."
### Step 5:Access Your Docsify Documentation
Once configured, your Docsify documentation will be accessible at https://your-username.github.io/your-repository/.

## Docker
### Step 1: Create docsify files

You need to prepare the initial files instead of making them inside the container
>index.html  
README.md
### Step 2: Create Dockerfile 
```
FROM node:latest
LABEL description="A demo Dockerfile for build Docsify."
WORKDIR /docsify
RUN npm install -g docsify-cli@latest
EXPOSE 3000/tcp
ENTRYPOINT docsify serve .
```
The current directory structure should be this:
 >index.html  
 README.md  
 Dockerfile
 
### Step 3:Build docker image
```
docker build -f Dockerfile -t docsify/demo .
```
### Step 4:Run docker image
```
docker run -itp 3000:3000 --name=docsify -v $(pwd):/docsify docsify/demo

```

