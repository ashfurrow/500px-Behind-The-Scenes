# Introduction

<!-- Slide: Logo -->

<!-- Slide: About -->

Good afternoon. My name is Ash Furrow, and I'm the Lead iOS Developer at 500px. I've been developing iOS applications since 2009 and taught an iOS development workshop at my university. After graduating from the University of New Brunswick last Summer, I moved to Toronto where I planted myself firmly within the iOS Developer community here. I have co-authored a book on Objective-C, regularly update my blog on the pain points of Objective-C, and now I'm giving a talk at Screens.

Today, we'll be taking a look back at the experience 500px has had in building our native iPad app: what we did, why we did it, and what we learnt in the process. This talk isn't specifically geared towards developers; if you're involved at all in mobile software development, I think you'll this interesting.

<!-- Slide: iPad app on iPad, website screenhot in Safari window -->

500px is a community of professional and aspiring photographers who upload their best photos to share with other photographers and photography lovers. Unlike other photographer communities on the web, 500px focuses on quality of work, not quantity. The website is known for showcasing the fantastic user content with large photos and thumbnails. The design of the app followed that of the website: the interface was sparse and as minimal as possible to let the photos occupy the user's attention. Let's take a look at what the app looks like right now.

<!-- Slide: Another iPad app screenshot (on iPad) -->

I started at 500px in late August, 2011 when the company still occupied a corner of Ryerson's Digital Media Zone. When I was interviewed for the job of 500px's iOS developer, I was shown some screenshots of the design for the app I would be making. While I already really wanted the job, after seeing the designs, I knew that *this* was the app I wanted to build. 

# Design

<!-- Slide: Design -->

<!-- Slide: Photoshop window with v1 mockup -->

By my first day, the designs for version 1 of the app were ready to be implmented and we with a rough roudmap of future versions and features. I initially, and optimistically, estimated that it would take 4 weeks to complete development.

<!-- Slide/Fade to app. -->

The design drew heavy inspiration from the built-in Photos application. There were two principle views: the thumbnail view where users would tap or pinch open photos, and the photo view, where users would see full-screen versions of photos, swiping back and fourth between them and seeing their metadata (name, comments, EXIF data).

<!-- Slide: Side-by-side of Photo app and iPad app, slide in/slide out -->

Drawing from the Photos app meant that users were already familiar with the interface, relieving friction experienced by new users. It also reinforced our core belief that it was our users' content that would make our app stand out. This app would adhere to user's expectations and gain their trust, which is very important to us. 

What we learned here is not to overlook the system apps when deciding on inspiration for your design. These apps are familiar to users and re-using paradigms in them will help your users trust your app. Other apps, like Facebook, Path, and Pinterest, opt to create their own new interface paradigms. That's fine for Facebook, but we always considered sticking to what our users already know before branching off to do our own thing. Even if we had decided to diverge from the established interface paradigms, there is still value in keeping them in mind while designing our app. Let's talk about what we mean by that. <!--rephrase to make it clear that we're not anti-new ideas, or that we're against contadicting the HIG, just that it's an important decision not to be made too lightly.-->

<!-- Slide: Close up of the sidebar, blur right side of the app -->

The 500px app does depart from the established guideliness in some ways. The sidebar is used to navigate between the different feeds, like Popular, Editor's Choice, Upcoming, etc. While this is a novel interface concept, it draws inspiration from a paradigm users are already familiar with: the tab bar. Our side menu looks and and behaves exactly like a tab bar that's been turned on its side. The icons represent a different perspective on the same data, the currently selected item is highlighted, and each item has a monochromatic icon with a subtitle. Just like a tab bar.

This should highlight how, even if you blaze your own path, you can still value from keeping the established interface guidelines in mind.

<!-- Slide: Slide over iPad to show the photo thumbnails -->

Most of the screen, on any view of the app, is taken up by photos; what isn't is mostly black. When the first version was designed, the majority of iPads were the first generation, which only came in black. Black focuses users' attention on the photos and photo metadata text, where applicable. We tried to keep it distraction free. Refraining from adding any design or style that was unneed. This marks another departure from what Apple has established as common interface design, but again, our app is about the photos, not the interface.

The sidebar on the side was chosen to maximize screen real estate. We suspected that most users would use the app with their device in landscape mode, where there are more horizontal pixels than vertical ones. Since releasing our all, we've noticed that sidebar menus in iPad apps have become popular, which we find pretty interesting.

<!-- Slide: Google Analytics logo and wordmark -->

The next thing I want to talk about with regards to design specifications is Google Analytics. We planned to include Google Analytics tracking so we can gain insight into how users use our application. This is *critical*. You may think you know how users use your app, but you probably don't. <!-- Slide: Tracking popups --> We didn't. Even if you observe people using your app, this is only mimicking real-world use. Using analytics, we can make fact-based decisions about future version of our app. If you know that 90% of your users never use a feature that lots of people request, you know that the interface to access that feature isn't apparent enough. If you know where in the world people use your app, you can decide which languages to translate it into. If you know how long the average user spends in your app, you can use that in your investor pitch. Analytics will help you if you use it correctly.

We expected users to open the app, tap on one photo, and stay in the Popular feed for most of the app, swiping from one full-screen photo to another. However, we found out from our analytics that that's only half the story. Many users return to the thumbnail page briefly before returning to a full-screen photo. We didn't expect that at all.

<!-- Slide: Previous slide, animate "Track all the things!" (All the things cartoon) -->

Track everything. I mean *everything*. Google Analytics has a fairly decent SDK, but you can use others, like Flurry, if you want to. Track your app separately from your website. Track page views to discover the most common use cases of your app. Track events to find out what people are actually doing. Track operating system version to determine when it's appropriate to drop support for older version and make your developer's life easier. Track how many users are logged in and logged out. 

All this data is going to be useful when designing subsequent versions of your app, making marketing decisions, or pitching your company to investors. 

Luckily, we were building an app for a website that already exists with lots of analytics data, which helped inform our design. For instance, we knew what languages we needed to translate our app into for version 1.

# Development

<!-- Slide: Development -->

I worked one-on-one with our designer, Adam Shutsa, who devoted his full-time to this app. Working one-on-one was an amazing experience and we both learnt a lot about the design and development processes. Adam wasn't shy about imposing his designer suggestions on my development process, and I learnt to not confine myself in the developer world. We worked back-and-forth as we designed and developed the application, in a sense, co-developing and co-designing at the same time. 

I started voicing my concerns over a design, which Adam took seriously since this was his first mobile app and I had experience as a mobile developer. For instance, I once pointed out that a group of buttons was too close together to distinguish touches for Apple's minimum recommended hit area of 44x44 points. Another example is the highlight added around thumbnails as the user touches them; this visual feedback was inspired by how I knew the system's built-in buttons were implemented. When I suggested this to Adam, he thought it was a great idea and we designed the interaction together. These aspects of the implementation affected the design of the application, and by voicing my concerns, our application benefited from a better user experience.

<!-- Slide: Ash with Safari hat, Adam hiding in the jungle -->

The best way to approach a designer with an idea or critique is to remain calm. Avoid sudden movements. If they seem apprehensive, approach slowly. When threatened, a designer is likely to retreat, put on their headphones, and return to Photoshop. 

If you have an idea for a design, don't be shy about voicing your opinion. However, be construtive. Offer facts and evidence to back up your opinion. Apple and Android both have documented Human Interface Guidelines. <!-- Slide: "Yes, Android has a HIG, go figure" --> Rely on them. Present alternatives and work with your designer to come up with a list of pros and cons so you can make an informed decision together.

Sometimes, a feature is too dificult to implement. Few aspects of a design are impossible, but many are intractably difficult and won't fit within a budget or deadline. Whenever I came across one of these situations, I let Adam know as soon as possible. I explained why it was difficult. It might have been critical to the entire app, or it might have been worth setting aside for a point release. Those types of decisions we found we should make together. *Turns out* 

During development, we made sure that these changes and enhancements to the design did not compromise our core philosophy and original intentions. Other apps, even other apps using the 500px API, were released during development and it was tempting to look to them for changes to make to our designs. However, we continued with our original design, only bringing in what new ideas made a better interface and user experience. 

<!-- Slide: "Automatic Reference Counting (ARC)" http://en.wikipedia.org/wiki/File:LLVM_Logo.svg -->

Being the only iOS developer in the company meant I was the Lead iOS Developer. This was really cool, since I had complete say over a lot of aspects of the development process. It also meant that I had a lot of responsibility to ensure a smooth launch. While I adopted Apple's new Automatic Reference Counting technology as soon as it was stable, I did so with the calculated risk that something might go wrong. And indeed it did; I spent a few hours hunting down a bug in their compiler. However, the time I spent doing that was more than made up for in a simpler, more modern codebase. 

Another aspect of development I want to touch is the idea of "good enough implementations." Our version 1 wasn't going to be a masterpiece by any stretch. We wanted an application built that did what it was supposed to really well, but that doesn't mean that my approach to implementing features always had to be optimal. Far from it. I shipped code in the first verion of the app that today I am ashamed of. 

Really! I've learnt a lot in the year that's followed our launch in the app store, and how I implement features today is vastly different from how I implemented them last September. But last September wasn't the appropriate time to learn about the optimal way to do certain things. 

Let's talk about a few examples. 

<!-- Slide: "Table View" iPhone simulator with Table View -->

iOS encourages use of an element known as a "table view." It's used to present tabular data to the users and it is very efficient. It's this efficiency that let's it display hundreds or thousands of rows of data while taking up only a very small memory footprint. However, when providing cells for table views, you have a few different approaches. One of them is very fast and easy to implement, but is very costly to render at run time, slowing down performance on the table view these cells are contained in. Another approach requires time and effort to implement, but is incredibly efficient at rendering its content. 

Version 1 of our application used the first, easy implementation. A subsequent point release used the faster method. Sure, some users did notice the slower animation in table views, and that took away from the overall experience. But, in the mean time, *they were using our app*. Would my time have been better spent delaying our launch by a few more days to get this feature *as fast as possible*? Not at all. The best part is that when we released the update that improved the efficiency of the cell rendering, *users noticed*. They saw that we were dedicated to improving our app, constantly adding value to their experience. Users who contacted us about the slow animation thought that they had a stake in our app since it was *their feedback* that the app was too slow that lead to it getting faster.

This is a small lesson, and in the end, most users didn't notice the slow performance. But it shaved off more time from our initial launch and got the app into the hands of users faster. 

In that case, this performance problem was user noticable, and it was addressed very quickly after we released the app. Let's take a look at another example where a good-enough implementation saved us time, but wasn't something our users ever noticed.

On the cover screen, which the users first sees when they launch our app, we have some chevrons pointing to the left. These shimmer and, after a few seconds, the text "Slide to Discover" is overlaid on top of the chevrons. This is key to our user's first experience, since our gallery view scrolls horizontally instead of vertically, which users are probably more familiar with. This training is really important, and since it's the first thing the user ever sees when they interact with our app, it's important that it looks amazing.

The shimmering chevron animation was too hard for me to implement a year ago. I couldn't think of any way to do it that wouldn't take up at least several days of my time. But I knew that, while the user was on this screen, the application was handling a relatively small performance load, so I had more CPU, GPU and memory resources than normal to implement this feature. 

<!-- Slide: Chevrons -->

So I did something really basic. I got Adam to produce, using photoshop, 14 PNG images representing keyframes of the shimmer animation. I then set up a timer that, every fifth of a second, replaced the existing imange with the next key frame and added a cross fade animation that took up a tenth of a second. Rinse. Repeat. 

It wasn't pretty, code-wise, but the effect was very convincing. It took about a half hour to implement before I moved on to something else. Today, our app uses a much more sophisticated animation that does, sure, look a lot nicer. But nobody noticed and I got to come back to the shimmering animation when I had the expertise to solve it the right way, months later. 

In these cases, we saw that early optimization could have lead to delays, but by taking the approach of implementing a feature and refining it later, we managed to get our application in the hands of users faster and at a very small cost.

Around week 4, we had enough core functionality finished that we were ready to start external testing. Lots of features, like the slideshow or commenting, weren't finished yet, but we knew that the more beta testing we performed, the better. Luckily, around that same time, TestFlight was taking off (*pause briefly for effect*).

<!-- Slide: TestFlight logo -->

TestFlight provided a really conveient way to distribute beta builds of our app. Almost as importantly, however, it provided an easy way to recruit beta testers. We used the company's twitter account as the primary way to recruit testers for the first version of the app; we changed tactics slightly for betas for point releases, which I'll discuss in a few minutes. Collecting device identifiers from prospective beta testers, playing email tag with them, and distributing signed copies of the executable with instructions on how to install it, possibly over top of an existing install, had historically been a huge pain in the ass for iOS developers. Complicating matters is the fact that some of your users are even running Windows. 

TestFlight worked really well for us. I had a few problems distributing builds of our app without incrementing our build numbers, so I integrated a Ruby script into Xcode that incremented our executable's build number every time I built it. (Aside:) Even though little things like that take a small amount of time, I found that investing a few minutes into automating these types of processes eventually paid off in solving headaches down the road. 

We never used TestFlight to its full potential, using their API to collect events or soliciting feedback from beta testers from within the app. What was most useful to us were crash reports. We used the system logs to reproduce bugs that causes crashing issues, so always err on the side of superfluous logging. 

I really can't stress enough how important it is for you to use TestFlight or a comparable system for recruiting testers, distributing builds, and collecting beta crash reports. Find what features are important to you, and if you're so inclined, you can even use TestFlight to distribute designs you're not sure you want to commit to in your production app. Just be sure to manage your testers expectations, and if you need confidentiality, make sure that's understood up front.

We used Test Flight and connections my bosses had to get our beta in the hands of GigaOm and Sarah Lane, who reviewed the betas publicly. This generated considerable buzz, and only a little panic when the Sarah Lane discovered a bug in the app live on *This Week in Tech* <!-- It was actually iPad Today, but TWiT is cooler and bigger -->. 

<!-- Slide: Flags of the languages we supported -->

Finally, let's talk about the localization of our app. We launched in 6 different languages: English, French, Russian, Spanish, Portuguese, and German. We've since added Italian and Dutch <!-- Slide: Fade in Italian and Dutch flags -->, but still have quite a few to add. We launched with so many languages because we knew from our website stats that 500px has a worldwide audience. We were able to leverage that audience to help us translate the strings in our application to these different languages, which we're really grateful for. <!-- Screenshot of About screen -->

This is kind of a double-edged sword, though. Many language have translations done before we even ask for them. The Germans are *incredibly* efficient at translating, surprising no one. Other languages remain at 20% done even today. These fringe languages aren't as popular among our users, so we haven't pushed for them, but we're planning on improving our support with an upcoming release.

<!-- Slide: Stacked iPads displaying lower right of Photo view in different languages -->

User-visible strings in our application fall into one of two categories: either it represents the content on the website, like a photographer's name, or it represents static text we ship with our application, like the English words "Photographer Name." These second group are the words and phrases we translate into other languages.

The issue is that, while we lay out our user interface with the English text, when we translate that text and replace it at runtime, the layout needs to still look stunning. There are a few different ways to approach this, and we chose the path of laying out text like this dynamically, using code, at run time. This cost us a little flexibility to see all of the different interfaces laid out with their respective translated strings. Instead, we had to change our device to a different languages and re-run our app.

There is a lot of code I had to write just to reposition the different labels and other UI elements depending on their size at runtime. It's code we need to maintain, but I'll talk later about how dropping support for older version of iOS makes localization faster.

# Release

<!-- v1.0 hash is 3f46f4d0901396ce527fc9801931e32bf55cdb82 -->

The first version of our app was released to the App Store on October 14th, 2011. <!-- Slide: Screenshot of v1 on iPad --> I'll always remember that date; it was actually a traumatic experience for me. When submitting an executable to Apple for approval, developers have two options: release the app as soon as Apple has approved it, or hold it for developer release. Since we wanted to get it out as soon as possible, I figured we may as well just release it whenever Apple finished approving it. What I didn't expect was that to only take a few days. 

My parents flew into town Saturday morning, only a few hours after the app had hit the store. I had to balance family time with responding to Twitter, my bosses, and Adam. It was less than ideal, but after 7 weeks, the app was finally live.

<!-- Slide: Fireworks over top of iPad -->

Our users had been anticipating our app for weeks. Pictures of its development had been leaked by my boss on Instagram, <!-- Slide: Evgeny's Instagram photos --> which actually caused problems for us in terms of managing users' expectations. We saw a huge spike in downloads in the days that followed the initial launch. In the first week, the app had been downloaded by more than a hundred thousand users. We were ecstatic. In the top free apps charts, we were listed higher than Netflix. <!--Insert screenshot from the store here on slides--> 

The tech media covered us extensively; we had articles on the likes of TechCrunch as well as photo blogs reviewing our app. We didn't *plan* on any of this coverage, so it was awesome that we got it. In hindsight, we should have been more coordinated and prepared for a launch with our own PR. Everything worked out for us, but now we always make sure that we coordinate with our PR guys. 

When Apple launched the iPad 3 with the Retina screen, the devices they distributed to the media actually had our app pre-installed to show off the screen. We're incredibly proud of that.

Users started leaving ratings and feedback, and we were averaging four stars in the app store, which is really good. Any ratings is better than no ratings, even if they're bad. Ratings help us rank higher in search results and also influence Apple's decisions to feature us in different sections of the App Store. We've been featured in the Photography and Social Networking categories, and whenever Apple features us, we see a significant bump in the number of users downloading our app. 

At first, people were just excited that we had an app at all. They were leaving 5-star reviews out of sheer gratitude. Eventually, however, their gratitude faded and we started being subject to the harshness of App Store reviews. Users would leave 1-star ratings because we didn't have a certain feature they wanted. Our application was just for *viewing* photos on the site and not for organizing them or uploading new photos. Users would leave reviews stating that they would change their 1-star review to a 5-star once we added uploading. 

It is *incredibly* frustrating to read these reviews. They hurt. When you pour every minute of your professional day into building a smooth, highly-polished product someone pointing out the nicks in your product hurts. <!-- Slide: Animation of equation, footnotes of source --> App Store reviews are anonymous, and regular people, plus anonymity, plus audience equals jerks. <!-- source: http://www.penny-arcade.com/comic/2004/03/19/ --> 

We've had to learn to not take these personally, and that's been really hard. The fact is, users don't know that they're hurting our feelings. They don't know that, when they demand that "the entire iOS team needs to be fired and replaced", they're talking about one guy. Any they can't be replied to.

That's the truly frustrating part: if someone has a genuine concern, Apple provides no way for us to support that user or contact them in any way. It's incredibly frustrating, but is part of being in the iOS App Store.

Circling back to the idea of analytics, we had some impressive stats. users were using our app, on average, for more than 45 minutes at a time. <!-- Slide: "45 Minutes" --> That's amazing! Most users don't even use websites that long, and iOS devices lend themselves to being used for brief periods of time. Having an application that people use for well over half an hour is something that we are incredibly proud of.

We also noticed a common usage pattern. Most users open the app, see the popular feed of photos, and tap a photo right away. Then, then slide forward to the next photo. And the next. And the next. <!-- Slide: Thumbnail with arrow to full size, with arrow to full size, animate more and more, very fast --> For 45 minutes. Some users will return to the Popular gallery before opening another photo and exploring the feed from there. 

Knowing that most users spend most of their time looking at fullsized photos has influenced design decisions, which I'll talk about shortly. The important thing for us is that we had these analytics from day one and we use them to make informed, fact-based decisions about our designs that reflect real-world use.

# New Features

<!-- Slide: New Features -->

The 500px team moved into our first office space mid November. Things were hectic, as always, and Christmas was fast-approaching. There were so many features that we didn't include in version 1 - Adam had been spending all the time I was fixing bugs designing them so I could get going as soon as possible, so that's what we did.

<!-- Slide: Screenshot of Profile view -->

The first thing that users really wanted is the ability to see another user's profile, even their own profile. Profiles include things like the user's photos, their bio, their avatar, and their gear. Photographers love to compare gear. We also wanted to let users follow each other in the app, something they could only do on the website. 

Luckily for our users, we had been planning this in our first point release all along. Adam re-used the design aspects from the main gallery page to show of users' photos. By the time someone using our app reached another user's profile, they were already familar with the interface. I re-used a significant portion of the code used in the main gallery, as well, so developing this feature was pretty fast. 

This app runs on an iPad, and an iPad is never upside down or sideways; <!-- Slide: iPad with 4 Up arrows around each side --> the interface of a good app adjusts to whatever orientation the user is holding their device in, despite the fact that we knew most users use the app in landscape orientation. The user details page was fun to design and implement because it tailored the layout of the same information depending on the orientation of the device. While this was fun, it also has caused some problems. Most interfaces in most apps just stretch when rotated, but this one actually pivots around the lower righthand corner. Stepping outside the box involved a little extra work, but we feel it is worth it. 

Let's talk about evangelising. Chances are, if you're at a startup or on your own, you don't have an in-house marketing team, or a PR person, or maybe even a customer support rep. We had a support rep, Diana, but she was pretty overwhelmed with support requests on the site (we later hired more reps). Often times, I would get forwarded emails from Diana. 

And you know what? I loved it. 

Beyond the cliched "keeping in touch with your users" thing, I got a direct opportunity to help users in a meaningful way. It was really satisfying, kept my eyes on what's important (pleasing the users), and only took up a few minutes of my day. What's more important than how I felt was how the users felt.

When a user contacted our support email address, they're doing so because we failed to meet their expectations in some way. Every time. Every time a user is so concerned about a facet of their experience with our product that they go through the effort of composing an email, they're doing so because we failed to meet their expectations and they care about it. I had the opportunity to completely exceed their expectations by replying directly. Users don't expect someone with the title "Lead iOS Developer" in their email signature to reply (and they certainly don't know that I was the "only" iOS developer). They don't expect to have the ear of the person who is directly accountable for their experience as a user. 

I began every email with "Hi, thank you so much for taking them time to contact us. We really love to hear from our users. I'm really sorry that you're having this problem..." I ended every email with "Thanks again for getting in touch. If you ever have any feedback on our app or the site, please don't hesistate to let me know!" 

Users loved it. They loved it because it showed them that their concerns were important enough to demand the attention of someone who could actually help.

Since users who contacted us did so because they care, I took the strong, negative feelings they had and turned them into strong, positive ones. I took the users who were upset enough with us to contact us and explain why they were upset and I turned them into evangelists who love 500px because we listened to them. Because *I* listened to them. It took a small amount of time out of my day, but it helped us so much in the long run that it was so, so worth it.

Users who were really mad would contact support or write an app review, but most users don't care that much. Instead, they turn to twitter. Adam was great at managing our twitter presence, looking for users with feedback. He actually has a bookmark for the Twitter page searching for our app name. This was another opportunity for us to exceed the expectations of users who we had previously let down.

However, some users are just plain mad and there is nothing we could do to satisfy them. The best thing we found to do, just like angry App Store reviews, was to ignore them. Don't feed the trolls, so the saying goes.

We were getting feedback from users that they wanted to filter photos in our app by category. For instance, users wanted to see popular photos but only ones that were landscapes, portraits, or black and white. This is a feature that our site has and it was something we felt was important, and relatively easy, to incorporate into our app.

<!-- Slide: Screenshot of Category Select popover -->

A standard user interface convention for filtering results is to tap-and-hold on the button representing the content you want to filter. We stayed within the conventions of the system and implemented filtering by categories by tapping and holding on any of the sidebar buttons to present the user with a popover where the could filter photos. It was a solid implementation that we were proud to put out in a point release.

However, feedback from users asking for this feature never stopped. People were still asking for the ability to filter photos by category, even though the app already supported this. When we would respond to user support inquiries explaining where to find this feature, they were all happily surprised and satisfied, which is good news! But why weren't they finding this feature on their own?

Even though we had adhered to the conventions of iOS, users couldn't find the feature they were looking for. We wanted to keep our interface as small as possible, so a "Filter" button was out of the question - especially considering the relatively small number of users requesting this feature. How could we make an interface more obvious while also keeping it minimal?

We couldn't. So we chose to stick with our core principle that the app should always be first and foremost about the photos. Instead of making our interface more obvious, we changed the app's description in the App Store to add instructions on how to filter by categories. When we added a video tour of the app, we highlighted this feature. Users still occasionally asked us about this feature, and we always thanked them for getting in touch, we told them how great it was to hear from our awesome users, and we explained where they could find the feature. 

Months later, I had the opportunity to have an Apple User Interface Evangelist dissect our app. After they were done, I asked them about our category feature problem. They said that we did everything correctly, that the interface was great, and that this is how Apple would have designed it, as well. 

At the end of the day, you need to try to make most of the people as happy as possible. We learnt that sometimes, in spite of all of our efforts, some users will have a less-than-optimal experience. All we can do is make things as apparent as possible without compromising our design and respond to these users privately and politely. 

<!-- Slide: Crashlytics logo -->

Late in 2011, Crashlytics was becoming a big deal. Crashlytics is a service that provides a library you build into your appplication when you submit to the store. When your application crashes, not *if* it crashes, it generates a crash log that's accessible. Crashlytics will upload this log to their servers the next time the user launches the app. The log is then symbolicated and sorted, giving you a really convenient place to list all the crashing issues in your app in order of severity. 

We were one of Crashlytics' first, popular apps. We get along great, and they tout our adoption on their homepage. I would highly recommend them. Regardless of what you use, you need to be collecting these reports. Your app *will* crash and if you care about that at all, you need to collect them.

# Maintenance

<!-- Slide: Maintenance -->

Just before Christmas, we started releasing new betas to our external beta testers that didn't add the features they wanted, but improved things like performance, battery life, and bandwidth used by the app. Since these improvements weren't super-sexy and sought-after, we found our beta testers, who had previously been super awesome, were nowhere to be found. 

What was worse was that we were butting up against a limit to the number of devices we could install our app on, imposed by Apple. They since softened their rules around this, but at the time, we had beta testers who weren't testing but were taking up valuable slots.

So while beta testing was really useful for finding bugs when we were in development mode, we found it to be less useful when maintaining the app. 

One big change we made around this time was to adopt Core Data. Core Data is used to temporarily persist objects in memory to disk, letting the application hold more object in memory than could fit in RAM. Ideally, we would have already have been doing this, but at the time, it wasn't important. Our implementation of throwing out data when we ran low on memory and re-fetching as required was good enough to ship, so we shipped it. Now it was time to mature the app a little bit. 

Adopting Core Data saved us bandwidth and API calls, as well as the responsiveness of the application. However, it does so at the cost of code simplicity. A Core Data object can only be accessed by code execution on the thread on which the object was created. Network-layer code to fetch JSON from our API had to be re-architected to support this new way of dealing with models. 

This was a significant change that was finished just before Christmas. I had worked really hard on it and was eager to get the new code into the hands of our users before the Holiday season. Our beta testers were missing, we didn't have any QA engineers at the company, and I hadn't written unit tests or integration tests for the code base. In hindsight, this was pretty stupid, but we forged forward.

The app was released a day before Apple shut down the app approval office for almost two weeks. It was very broken, and it haunted me for my entire Winter vacation. Even though I had fixed the problems, I couldn't even submit the app for review until January 1st, and even then, it still had to wait in the queue for Apple to approve it. We managed to work with them to expedite the process, but it still left our users with a broken app for two weeks, which is completely unacceptable.

Now, before making architectural changes, we have integration tests and unit tests to ensure we didn't accidentally break anything. It was a hard lesson to learn, and we took a beating in the app store reviews.

In early 2012, we were still supporting iOS 4, even though iOS 5 had been around for four months already. Support both doubled the effort for some common tasks, since Apple changed much of the underlying mechanics of their user interface library between these major versions of iOS. We had a lot of code like this. <!-- slide of if (iOS4) DO THING else DO OTHER THING --> In addition to alleviating repeated development effort, requiring iOS 5 as a minimum would allow us to use new, sexy libraries that Apple introduced, so I was very eager to do it. Adam was skeptical. 

Dropping iOS 4 support meant that existing users would be forced to upgrade their iPad's operating system, but it didn't remove support for any hardware. This meant that any users who had the app would still be able to use the app, they just might have to upgrade their OS.

<!-- Slide: Ticker of 87% 88%, 89%, 89.5%, 90%. iOS4 logo disappears -->

We agreed that we could drop iOS 4 support when 90% of our users had upgraded. We tracked this through analytics. Eventually, we pulled the plug and dropped iOS 4. My job got easier. New features were being turned over faster. When we shipped our first update requiring the new OS version, we were prepared for the worst. 

<!-- Slide: iOS 4 logo with tumble weed bouncing infront -->

No one complained. At all.

So while we waited for over 90% adoption of the new OS, we could have probably dropped it even sooner, making my life easier and almost no cost. Supporting only the latest iOS version is really easy. Since then, Apple has made the experience of upgrading an iOS device's operating system nearly painless, so we don't hesistate to require the point releases of iOS. 

iOS 6 introduces some new, really exciting APIs for localizing interfaces that makes laying out interface elements very easy. I mentioned earlier that we have a lot of code dedicated to laying out interfaces in different languages where text is longer or shorter. Apple has made it a lot easier in iOS 6, and I can't wait to drop iOS 5 support. 

However, we still require iOS 5 or higher, and dropping support for it is a bigger problem now. If we drop iOS 5 support, then iPad 1 users will be unable to use our application. This generation of iPads account for about 15% of total iPad marketshare, which is a significant amount of users. We're still not really sure what to do about that.

# More New Features

<!-- Slide: More New Features -->

<!-- Slide: In-App Purchases screenshot -->

Since the beginning of the year, the iPad app has made some really interesting and hard-fought progress on some key features. We adopted Apple's in-app purchases for downloading high-resolution copies of  photos. Of course, we give that money to the photographer, so we don't really gain anything financially from this feature. However, it makes our app more feature-rich and makes our platform more attractive to photographers looking for a way to sell their work online.

<!-- Slide: Notifications screenshot -->

We also integrated push notifications for events like when someone comments on a photo of yours. This marked the first feature we added specifically for photographers. Even though our website is for hosting the world's best photography, many of our users are only photography lovers. Our iPad app was designed to be the best experience we could make of *viewing* those photos. It's really an app for these photography lovers. With push notifications, we added a lot of value for users who are photographers as well as photography lovers. 

After dropping iOS 4 support, we circled back to the original designs Adam made. Many of the customized interface elements that Adam painstakingly designed had to be ignored or heavily modified to fit within the constraits of the user interface library that Apple provids in iOS. That was in iOS 4. iOS 5 introduced rich new APIs that made customizing the appearance of the built-in controls very easy.

So we looked at the designs and overhauled every pixel of every view to bring it in line with our design. It only took a week or two, but the results look fantastic. This was actually one of the things I used to convince Adam dropping support for iOS 4 was a good idea. It's not easy to go up to a designer and explain how conditionally linking against different libraries would make things hard, but it's really easy to go up to them and say "hey, you know that design we couldn't implement before? Well, we can, but only if you let us drop older OS support."

<!-- Slide: iPad slides in from the bottom showing the new nav bar. Another iPad slides in from the top showing the new Photo Details bottom bar -->

Our team has grown significantly. We employ three-ish full-time iOS developers. See, it's a start up, and most of us wear different hats. I don't, but most of us. I focus 100% of my time at developing this application, and we're finding that getting specialized developers to work on iOS or Android is the best to ensure progress on those platforms. It's hard to find someone to fill those roles, but sharing developers with the web team is hard, since the types of problems we solve fall into such distinct wheelhouses. 

I still lead the iOS Development Team, which means I still make the rules. We adopt new Objective-C language features and compiler versions as soon as they're stable. Adopting these means faster turnaround of features. We contribute to the open source projects we use ourselves and distrubte the fixes and improvements we make to them back to the Objective-C developer community. 

Now that I'm leading more than a team of just myself, my role in the company has changed somewhat. I'm growing into my new role and I'm looking forward to the new problems we're going to be dealing with on our iOS app.

This Summer, 500px hired its first QA engineer, and I'm really excited about having him on board. We're adopting new testing practices, or at least ones that are new to us. Unit testing, integrating testing, and automated user interface testing are helping us ship better code. 

# The Future

We are striving for feature parity with the website, but we have a long way to go. With every new release, we want to provide a more complete experience for our users. Having a completely feature-complete app is a fantastic goal, but in practice, it's very hard to achieve. Adding new features to the website is relatively easy and we can amend these features at any time. There is, at minimum, a week turnaround time for releasing an update to the iOS app, which means we need to be more vigorous in planning and testing our features. Also, the web team at 500px is bigger than the iOS team. I'm not bitter - I'm pretty happy that the app I wrote handles half the amount of traffic that our web site handles. 

Our codebase is expanding. At last count, we peaked over sixty thousand lines of code. With all this code, we are accruing a maintenance deficit that we are finding we have to address with each release, and it is slowing down the progress of new features. This is where our integration and unit testing plan comes in to help us.

We've got some really exciting features that are just over the horizon, and I wish I could share them with you, but you'll have to wait. 

We are hiring. If you're interested in working with us, in any capacity, we'd love to chat, so get in touch. If you have any questions about anything I've talked about today, I'd love to get in touch. I've got a blog where I regularly discuss the nitty-gritty implementation issues I work with every day, and I'm on twitter. 

Thank you.


