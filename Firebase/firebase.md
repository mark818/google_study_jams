# Firebase介绍

## 背景

> Firebase is a mobile and web application development platform. Firebase is made up of complementary features that developers can mix-and-match to fit their needs. The team is based in San Francisco and Mountain View, California. The company was founded in 2011 by Andrew Lee and James Tamplin. Firebase's initial product was a realtime database, which provides an API that allows developers to store and sync data across multiple clients. Over time, it has expanded its product line to become a full suite for app development. The company was acquired by Google in October 2014 and a significant number of new features were featured in May 2016 at Google I/O.

Firebase是一个移动与网页应用开发的平台。Firebase由一系列互补的功能组成，让开发者可以按照需求自由组合。Firebase的开发团队位于加州旧金山与山景城。公司由Andrew Lee和James Tamplin建立于2011年。Firebase最初的产品是一个实时数据库，提供API给开发者跨用户地存储和同步数据。在这之后，它逐渐的扩张了自己的产品线并成为一个应用开发的套装。公司在2014年10月被Google收购，并在2016年5月Google I/O宣布加入了大量新功能。

## 功能

截止目前Firebase已经有一条完整的产品线，成熟的一站式服务，并生成可以提移动应用开发者包办服务器后端的所有需求。

- Firebase Analytics
	- Firebase Analytics is a free app measurement solution that provides insight into app usage and user engagement.
	- Firebase Analytics是一个免费的app测量解决方案，为app使用数据和用户参与度提供建议。

- Firebase Cloud Messaging
	- Formerly known as Google Cloud Messaging (GCM), Firebase Cloud Messaging (FCM) is a cross-platform solution for messages and notifications for Android, iOS, and web applications, which currently can be used at no cost.
	- Firebase Cloud Messaging的前身是Google Cloud Messaging，它是一个跨平台的解决方案，为Android，iOS和网页提供信息和提醒，目前可以免费使用。

- Firebase Auth
	- Firebase Auth is a service that can authenticate users using only client-side code. It supports social login providers Facebook, GitHub, Twitter and Google. Additionally, it includes a user management system whereby developers can enable user authentication with email and password login stored with Firebase.
	- Firebase Auth是一项只使用用户端代码验证用户的服务。它支持社交登陆提供商Facebook，Github，Twitter和Google。另外，它包含一个用户管理系统，使得开发者可以通过储存在Firebase的email和密码登陆验证用户。

- Realtime Database
	- Firebase provides a realtime database and backend as a service. The service provides application developers an API that allows application data to be synchronized across clients and stored on Firebase's cloud.The company provides client libraries that enable integration with Android, iOS, JavaScript, Java, Objective-C, swift and Node.js applications. The database is also accessible through a REST API and bindings for several JavaScript frameworks such as AngularJS, React, Ember.js and Backbone.js.The REST API uses the Server-Sent Events protocol, which is an API for creating HTTP connections for receiving push notifications from a server. Developers using the realtime database can secure their data by using the company's server-side-enforced security rules.
	- Firebase提供一个实时数据库以及“后端即服务”。服务向应用开发者们提供一个API来使应用数据在用户之间同步并存入Firebase云。公司提供用户端库与Android, iOS, JavaScript, Java, Objective-C, swift以及Node.js的应用集成。这个数据库也可以通过Rest API和数据绑定访问。数据绑定可以选择数个Javascript框架如AngularJS, React, Ember.js和Backbone.js。Rest API使用服务器分发事件协议，一个与服务器创建HTTP链接来接收push和消息的API。使用实时数据库的开发者们可以使用公司的服务端安全规则保障他们的数据。

- Firebase Storage
	- Firebase Storage provides secure file uploads and downloads for Firebase apps, regardless of network quality. The developer can use it to store images, audio, video, or other user-generated content. Firebase Storage is backed by Google Cloud Storage.
	- Firebase Storage为Firebase应用提供安全的文件上传与下载，无论网络好坏。开发者们可以用它储存图像、音频、视频与其他用户生成内容。Firebase Storage由Google Cloud Storage提供支持。

- Firebase Hosting
	- Firebase Hosting is a static asset web hosting service that launched on May 13, 2014. It supports hosting static files such as CSS, HTML, JavaScript and other files that do not change dynamically. The service delivers files over a content delivery network (CDN) through HTTP Secure (HTTPS) and Secure Sockets Layer encryption (SSL). Firebase partners with Fastly, a CDN, to provide the CDN backing Firebase Hosting. The company states that Firebase Hosting grew out of customer requests; developers were using Firebase for its real-time database but needed a place to host their content.
	- Firebase Hosting是一个始于2014年5月13日的静态页面托管服务。它支持托管静态文件如CSS, hmlt, Javascript和其他不会动态变化的文件。这个服务在CDN中通过HTTPS和SSL交付文件。Firebase与Fastly，一个CDN提供商合作，提供CDN支持的Firebase托管。公司称Firebase Hosting出自用户的需求；开发者们在使用Firebase的Realtime Database但是需要一个地方托管他们的内容。

- Firebase Test Lab for Android
	- Firebase Test Lab for Android provides cloud-based infrastructure for testing Android apps. With one operation, developers can initiate testing of their apps across a wide variety of devices and device configurations. Test results—including logs, videos, and screenshots—are made available in the project in the Firebase console. Even if a developer hasn't written any test code for their app, Test Lab can exercise the app automatically, looking for crashes.
	- Firebase Test Lab for Android提供基于云端的安卓应用测试架构。只需一个操作，开发者们可以为他们的应用启动各种设备和设备配置上的测试。测试结果包括日志、视频和截屏。它们都在Firebase控制台可见。即使一个发开着没有为他的应用写任何测试代码，Test Lab也可以自动测试应用，寻找崩溃处。

- Firebase Crash Reporting
	- Crash Reporting creates detailed reports of the errors in the app. Errors are grouped into clusters of similar stack traces and triaged by the severity of impact on app users. In addition to automatic reports, developer can log custom events to help capture the steps leading up to a crash.
	- Crash Reporting为app中的错误创建详细报告。拥有相似堆栈跟踪的错误被归并到集群，并按照对应用用户的影响分优先级。除了自动报告，开发者们可以记录自定义事件来帮助捕捉导致崩溃的步骤。

- Firebase Notifications
	- Firebase Notifications is a free service that enables targeted user notifications for mobile app developers.
	- Firebase Notifications是一个免费服务。移动应用开发者们通过它向定向用户发送通知。

- Firebase App Indexing
	- Firebase App Indexing, formerly Google App Indexing, gets an app into Google Search. Adding App Indexing promotes both types of app results within Google Search and also provides query autocompletions.
	- Firebase App Indexing，前身为Google App Indexing，将app放入Google搜索。使用App Indexing既可以提升Google搜索的app结果类型，又能提供搜索自动补全。

- Firebase Dynamic Links
	- Firebase Dynamic Links are smart URLs that dynamically change behavior to provide the best experience across different platforms.
	- Firebase Dynamic Links是智能url。它能动态改变行为以在不同平台上提供最佳体验。

- Firebase Invites
	- Firebase Invites is a cross-platform solution for sending personalized email and SMS invitations, on-boarding users, and measuring the impact of invitations.
	- Fierbase Invites是一个跨平台的解决方案。它能发送个性化的email和短信邀请，加入用户，和衡量邀请的影响力。

- Firebase Remote Config
	- Firebase Remote Config is a cloud service that lets developers change the behavior and appearance of their apps without requiring users to download an app update.
	- Firebase Remote Config是一种云服务。它让开发者们可以改变他们app的外观和行为而毋须用户下载更新。

- Adwords
	- Adwords is Google online advertising service that integrates with Firebase to enable developers to target users using Firebase Analytics segmentation
	- Adwords是Google线上广告服务。它被集成进Firebase，使得开发者们可以用Firebase Analytics分段来定位目标用户。


- Admob
	- Admob is a Google product that integrates with Firebase and enable developers to Earn money by displaying engaging ads to a global audience.
	- Admob是一款Google产品。它被集成进了Firebase并使得开发者们可以通过展示吸引人的广告来赚钱。
