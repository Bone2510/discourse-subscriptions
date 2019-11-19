# Discourse Patrons

[![Build Status](https://travis-ci.org/rimian/discourse-patrons.svg?branch=master)](https://travis-ci.org/rimian/discourse-patrons)

The Discourse Patrons plugin allows you to set up a subscription based Discourse application. By integrating with the [Stripe](https://stripe.com) payment gateway and setting up this plugin to manage Subscriptions, you can start selling users access to content on your website.

You can try it out here: https://discourse.rimian.com.au/patrons/subscribe

See [Screenshots](#screenshots) below.

## Installation

* Be sure your site is enforcing https.
* Follow the install instructions here: https://meta.discourse.org/t/install-a-plugin/19157
* Add your Stripe public and private keys in settings and set the currency to your local value.

## What are Subscriptions?

Subscriptions are how you manage access to your content. There are two core components to make Subscriptions work for your Discourse application. These are **Products** and **Plans**.

A Product describes what the user gets when they subscribe. It has a *name* and *description* and most importantly, it is associated with a Discourse User Group. A product can have one or more plans.

A Plan is how you charge your users for the Product. Plans have *rates*, *billing intervals* and *trial periods*. A Product may have multiple Plans. For example: a yearly and a monthly Plan with different pricing. You can't change plans much once they are created but you can archive them and create new ones.

Together, Products and Plans make up Subscriptions.

It is **important to note** that untimately, your subscriptions are managed by the Stripe payment gateway. Stripe will handle the billing, etc at the required intervals and notify your Discourse Plugin when something happens. If you were to destroy your instance of Discourse, you will need to cancel all of your subscriptions manually with Stripe. Thankfully, Stripe has a [portal](https://dashboard.stripe.com) where you can manage all that.

## How to set up your Discourse app for subscriptions.

### Set up your payment gateway.

Firstly, you'll need an account with the [Stripe](https://stripe.com) payment gateway. This is how you manage your transactions.

When you get a moment, take a look at Stripe's documentation. But for now, you can set up an account in test mode and see how it all works without making any real transactions. Then, if you're happy with how everything works, you can start taking real transactions. See below for test credit card numbers.

### Set up your User Groups in Discourse

When a user successfully subscribes to your Discourse application, after their credit card transation has been processed, they are added to a User Group. By assigning users to a User Group, you can manage what your users have access to on your website. User groups are a core functionality of Discourse and this plugin does nothing with them except and and remove users from the group you accociated with your Plan.

## Enter your configuration details

When you create an account with Stripe, you'll get a public and private key. These are entered in the Discourse Patrons admin so your subscriptions can integrate with Stripe. There are different keys for testing and production environments.

## Testing

Test with these credit card numbers:

* 4111 1111 1111 1111

## Warranty

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS “AS IS” AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

## Credits

Many thanks to Chris Beach and Angus McLeod who helped on the [previous version](https://github.com/chrisbeach/discourse-donations) of this plugin. Many thanks to the Discourse team who sponsored this plugin! You guys rock.

## Known issues

* CSS is mucked up in Safari and probably Firefox too.
* The phone number isn't sent to Stripe

## TODOs

* Currency on plans isn't done.
* Admin pagination
* Confirm dialog CSS isn't the best.
* Check against other themes (works ok with light and dark)
* Validate the model properly. Not in the stripe component
* Show the transaction on the thank you page.
* Work out where to put the helper tests. Name collision!

## Screenshots

### Products Admin
![Admin Products](doc/admin-products.png)
### Product Admin
![Admin Product](doc/admin-product.png)
### Plan Admin
![Admin Plan](doc/admin-plan.png)
### Subscription Admin
![Admin Subscriptions](doc/admin-subscriptions.png)
### Subscription User
![Admin Subscriptions](doc/user-subscriptions.png)
### Subscribe
![Admin Subscriptions](doc/subscribe.png)
