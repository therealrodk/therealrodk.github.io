---
layout: post
title: My Capstone Project
postHero: /images/celebration.jpg
author: THEREALRODK
postFooter: <iframe width="560" height="315" src="https://www.youtube.com/embed/6fHA-WO_K-c" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
---

### Finished!

I turned in my capstone project to Bottega Tech over the weekend, and was excited to hear back today that it was accepted and approved. I am now a <em>certified</em> Full Stack Web Developer! Yay!

For my project I created a website for a client. Feel free to check it out here: <a href="http://pollysbirthbook.com" target="_blank">pollysbirthbook.com</a>. The client sells several books, with a focus on one specific book–the website's namesake–so all books needed to be readily available but the main focus of the design had to be on the primary book.

### *She's Got The Look!*

I chose to design this website in Rails because it allowed me to design custom logic into the backend. This was important because the client had specific needs as far as taxes and shipping, which will be discussed later.

I used Bootstrap 4 for the view, which gave me quick and easy access to responsiveness. This works well at all of the major breakpoints, but resizing the viewer will show a tiny area in which the primary images don't entirely stretch top to bottom in their container. As I mentioned in another post, however, I am just learning about CSS Grid, so I may refactor to fix this at some point. You wouldn't have noticed if I hadn't told you :)

In keeping with DRY (Don't Repeat Yourself) principles, and keeping the focus on the primary product, the hero section at the top of the home page is reused at the bottom of every one of the target market pages (Mothers, Fathers, etc.).

### Picture This

Clicking on the 'Store' link in the main menu will display a list of all the books currently available. When the Admin logs in, she is able to add new books, including uploading cover images. For this, I installed the <a href="https://rubygems.org/gems/carrierwave" target="_blank">Carrierwave</a> gem and set specific sizes for the main Product images and thumbnail images. In my local development, I implemented some internal logic that displays placeholder images from <a href="https://placeholder.com/" target="_blank">placeholder.com</a>, set to the thumbnail size.

Unfortunately, when attempting to upload the site to <a href="https://www.heroku.com/" target="_blank">Heroku</a> later, I discovered that they do not allow local image storage, so I had to exchange the Carrierwave gem for <a href="https://rubygems.org/gems/carrierwave-aws" target="_blank">Carrierwave-AWS</a>, so that I could store the images on Amazon's S3. Luckily, this was an easy process.

### *S.H.O.P.P.I.N.G. We're Shopping…*

Clicking 'View Details' takes you to a product-specific page where all of the details are listed, a product description is shown, and, most importantly, the 'Add to cart' button is displayed. This is where it gets interesting…

At first, I planned to implement my own shopping cart system, but when I got to that point I realized that my concept was kind of naïve. Then, I thought I could easily implement a pre-existing shopping cart, but this turned out to be false for a number of reasons. For one thing, this client makes very little on sales and therefore the paid options were out of the question. I searched for 'Rails shopping carts', and found several tutorials of varying complexity, which encouraged me. After a couple full build-outs, I soon learned that most of these contained syntax that is incompatible with the current version of Rails–a fact that I was not in a position to recognize by simply reading through the code, since I cut my teeth on Rails 5 and have no experience with the older syntax. It turns out that the newer Rails interfaces with Javascript differently, which was part of the problem. So, what to do?

Well, if you're me, you suck it up and *build your own!*

I built my shopping cart completely from scratch, but going through all of the failed attempts mentioned above gave me some different perspectives on shopping cart approaches, and gave me the confidence that I could do it effectively.

The approach I took may not work for everyone, but it worked in this instance. The general idea is that there are only four models in my entire app: Users, Products, Orders, and Order Items. This is the process flow:

1. User visits a Product page and clicks the 'Add to cart' button.

2. Necessary Product information is stored as an Order Item and the User is sent to Cart page. Order Items only store the Product ID (so that the Product details can be referenced later), User ID (for reasons that will be explained later), and the Quantity set by the User before they added it to the cart. 

3. On the Cart page, the Order Items are displayed in a list, along with their individual price, individual weight, and total price based on the quantity. This client is based in Utah, so they are required to add sales tax for Utah residents. When Users create an account, they are required to provide their address, which is used by the Cart to determine if tax should be applied and to calculate the tax based on the subtotal. At the bottom of the Cart page, a form with shipping information is prepopulated with the User's address. This information can be changed, if desired. The client has a requirement for increased shipping charges to specific states, and that is calculated based on the address information entered here. Note that there is no actual Cart model. Instead, the Carts Controller processes the necessary information so that when User clicks the 'Review & Checkout' button…

4. An Order is 'created' in the system and User is sent to the Checkout page. From the User's perspective, 'instantiated' might be a better word because no payment has been submitted, but internally an Order now exists. Orders store a lot of information, including Subtotal, Tax, Shipping, Total, Shipping Address info, User ID (of course), and an array of Order Items with their Quantity. If User returns to their Cart and changes anything, then clicks the 'Review & Checkout' button again, a new Order is created in the system. Unprocessed Orders are taken care of later.

5. Following the instructions in their <a href="https://stripe.com/docs/checkout/rails" target="_blank">documentation</a>, I implemented a button that can be used to submit credit card payments to Stripe. For security purposes, no credit card information ever touches the client's server. This button is located at the bottom of the Checkout page. Once User has reviewed all information and had the opportunity to change anything, they click the button and enter their information. Once the payment has been successfully processed, User is sent to a page where a printable receipt is displayed, though I set up the Stripe account to also email receipts after successful processing.

6. When an Order has been successfully processed, the responsible controller checks the databases for all Order Items associated with the User and deletes them (this is why Order Items have User ID's attached to them, as mentioned in #2, above). At this time, any unprocessed Orders that were created by the User returning to, and adjusting the contents of, their Cart, are also deleted, leaving only Orders that have actually been submitted.

7. Users can log in at any time to view the status of their Orders, because all information is displayed on their Profile page.

And that's it!

### Who's The Boss?

*Tony Danza, that's who!* And, if he were my client, he would be both a woman and the Admin for this webapp. It could happen!

For my actual client, I built in the ability to see two categories of orders: 1) all Orders ever, in a paginated view (thanks to the <a href="https://rubygems.org/gems/kaminari" target="_blank">Kaminari</a> gem), and 2) pending Orders, i.e., those Orders that have been submitted and need to be processed. When the Admin selects an Order, they can view all of the Order details, but only make a few changes. Most importantly, they can change the Order status to either 'Shipped' or 'Canceled'. There is also a Notes field, to annotate the Order, if necessary.

The Admin can also see a list of all Users, and delete them if requested, but cannot view User info.

### *This Is The End…*

This has been an amazing learning experience, and I feel much more confident in both my Ruby and Rails skills now that I have reached this point. Shortly before completing this project, some of the assistants from Bottega complimented me, one saying that he felt like he could speak to me as he would with an experienced developer, and the other saying that this was one of the best capstone projects any student had ever done. Either I'm a sucker for flattery, or I have created something to be proud of. What do you think? For my part, I know that I still have a long way to go before I am where I want to be as a developer, but this is definitely a milestone.

<!--

Use this to place images within the article. Use the pull-left and pull-right classes for placement.

<img class="pull-left" src="http://placekitten.com/g/400/200"
     alt="kitten">
-->