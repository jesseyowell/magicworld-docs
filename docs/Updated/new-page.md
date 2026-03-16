---
title: new Page
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
# 📝 Getting Started

In this guide we will be training our own custom fine-tuned model to use to generate images using the Leap dashboard.

You can use fine-tuned image models to generate AI avatars, assets, and more! 

By the end of this guide, you should have a custom model you can use to generate AI avatars like this:

<Image width="500px" src="https://uploads-ssl.webflow.com/631e7debd95a0a0b974074e2/6363eb691262862207c3259e_Frame%20116.png" />

A quick overview of what you'll need to get started:

1. An account on [https://www.leapml.dev/signup](https://www.leapml.dev/signup)  
2. Image samples to train your model on

And an overview of the steps we'll cover in this guide:

1. Creating A Model
2. Uploading Image Samples
3. Queueing A Training Job
4. Generating Images w/ Your Model

# 1️⃣ Creating A Model

To begin, we'll create a model that is trained on Alex, a team member at Leap. To do this, we'll use the LeapML dashboard.

To create a model using the dashboard:

1. First, navigate to Fine Tuning and click "Create Model"

![](https://files.readme.io/28c411f-Screen_Shot_2023-01-27_at_3.51.08_PM.png)

2. Next, add a title for the model (e.g. "Alex Model") and a subject keyword (e.g. "@me" which will refer to Alex) and click "Create"

![](https://files.readme.io/bbf4180-Screen_Shot_2023-01-27_at_4.31.45_PM.png)

# 2️⃣ Uploading Image Samples

Now add your image samples. You can train on people, objects, or styles. For our example we'll be training on Alex.

For best results, resize your image samples so that each sample is 512x512 (you can a website like [https://www.birme.net/](https://www.birme.net/) to do so). 

Also we recommend using 3+ images and making sure your subject is clearly in view. Next, click "Upload". 

![](https://files.readme.io/2b14382-screenshot_2023-01-27_at_4.40.36_pm.png)

# 3️⃣ Queueing A Training Job

Finally, once your image samples are uploaded, click "Train New Version" to queue training. 

![](https://files.readme.io/080e6e0-Screen_Shot_2023-01-27_at_4.48.54_PM.png)

You should get an email when your model is done training and ready to generate images!

# 4️⃣ Generating Images w/ Your Model

Once your model is done training you should see the status update to "Finished". 

Next to start generating images with your custom model, click "Try In Playground". 

![](https://files.readme.io/26b5bf7-Screen_Shot_2023-01-27_at_5.06.50_PM.png)

Now, in the playground you'll be able to generate images by clicking "Generate". 

![](https://files.readme.io/129774b-Screen_Shot_2023-01-27_at_5.20.52_PM.png)

Add the "@me" identifier to your prompt and try out a few example prompts to get great looking AI Avatars!

* Portrait Style 👉 "portrait of @me 8k photorealistic pretty young"
* Van Goh Style 👉 "8k portrait of @me in van goh starry night style"

![](https://files.readme.io/27e682e-Screen_Shot_2023-01-27_at_5.23.55_PM.png)

# 🔑 Additional Config

We recommend experimenting with different prompts and steps for best results. 

More steps will usually result in better images but take longer to generate. 

# 🚀 Wrapping Up

That's all for this guide!

Try it out for yourself and let us know if you have any questions. For additional support please join our [discord](https://discord.com/invite/NCAKTUayPK).
