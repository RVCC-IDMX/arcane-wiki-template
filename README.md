# Arcane Wiki Demo

This forked repository comes from a tutorial [How to Optimize Images on Netlify with the Cloudinary Build Plugin](https://spacejelly.dev/posts/how-to-optimize-images-on-netlify-with-the-cloudinary-build-plugin/) by [Colby Fayock](https://www.colbyfayock.com/) and its YouTube video [Automatic Image Optimization on Netlify with the Cloudinary Build Plugin](https://youtu.be/0YOnthePzxI)

In it he explains how to use this repo to deploy to Netlify and make use of a Netlify build plugin titled Cloudinary 

**Thanks Colby**

## Getting Started Locally

- Install dependencies

```
yan install
```

- Start a local development server

```
npm run dev
```

## Creating a Cloudinary Preset for Upload

1. Follow the tutorial to make a Preset at [Create Transformation Presets in Cloudinary's DAM System](https://youtu.be/F7pA-jYs6ew).
1. You need not create the exact one from the tutorial. I suggest you create a Preset that crops the image to a 400px wide image, mode scale, auto format and auto quality.

<img width="458" alt="Cloudinary edit menu" src="https://user-images.githubusercontent.com/13385801/199068076-1a5393bd-4889-41c2-b4e5-9e65c0516d48.png">


3. Save the preset giving it the name `arcane`.

---

## Deploying to Netlify

1. Deploy to Netlify using the build defaults it finds in the package.json file. 
1. It will first deploy without Cloudinary.
1. Consider renaming your site after a successful deploy.

---

## Configure the Netlify Build Environment with Your Cloudinary Account Information

1. Login to your Cloudinary account.
1. In the Dashboard take note of your Cloud Name, API key, and API Secret.

<img width="950" alt="netlify form for environment variables" src="https://user-images.githubusercontent.com/13385801/199065276-43fde53f-2f41-40c5-b79b-0b580f1f02eb.png">

3. In Netlify go to Site settings -> Build & deploy -> Environment
4. Add values for the CLOUDINARY_API_KEY and CLOUDINARY_API_SECRET to your Netlify build environment

<img width="970" alt="Netlify environment form" src="https://user-images.githubusercontent.com/13385801/199073264-28ac5e0f-5cb8-4714-8f90-0dc0bfb94b91.png">

---

## Install the netlify-plugin-cloudinary plugin

1. Go to your Netlify Team Overview page.
1. Click the `Integrations` menu button.
1. Search for Cloudinary.
1. Click the `Add build plugin` button for the selection.
```
Cloudinary
Automatically optimize your Netlify site images and deliver them in modern formats with Cloudinary.
```
5. Choose the site you want to add the plugin to.
6. If successful, the plugin will appear on the site's plugin page

---

## Add the netlify.toml file to your repository

1. Create a netlify.tom file in the root of your repo loading the netlify-plugin-cloudinary plugin.

```
[[plugins]]
  package = "netlify-plugin-cloudinary"

  [plugins.inputs]
  cloudName = "YOUR_CLOUDNAME"
  deliveryType = "upload"
  uploadPreset = "arcane"
```

2. Make sure the cloudName matches your Cloudinary Cloudname.
3. Push the changes to GitHub.
4. Monitor the Netlify build log looking for the Cloudinary plugin.

---

## Checking for Successul Plugin Installation and Deploy

There are multiple indications that the plugin deployed successfully.

1. The Netlify deploy log shows successful plugin actions.
1. There is a new folder in your Cloudinary with the files from this repository. 
1. The images in the site are served from Cloudinary.


