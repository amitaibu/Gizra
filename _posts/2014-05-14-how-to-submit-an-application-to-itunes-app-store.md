---
title: How to submit an application to iTunes App Store
tags:
  - AngularJs
  - Angular
  - iTunes
  - iOS
  - Android
  - Mobile
  - Apple
  - "iTunes App Store"
permalink: "/content/how-to-submit-an-application-to-itunes-app-store"
layout: post
published: true
---
{% include JB/setup %}

This article explain the process to submit and an application to the iTunes App Store. We assume that you already passed all the process of development an test your application.

<!-- more -->

## Requirements

* Create an account in a [iOS Developer](http://developer.apple.com/), the credential of this account will be use in the Create a certificate process.
* Create a XCode project an test the application.
* Configure your application for distribution. [Apple adiciotnal info](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW1)
* Tools: [Provisioning Portal](http://developer.apple.com/ios/manage/overview/), XCode, Keychain Access utility and [iTunes Connect](http://itunesconnect.apple.com/).

## Create unique App ID

* Open the [Provisioning Portal.](http://developer.apple.com/ios/manage/overview/)
* Select Identifier

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/provisional_site_main.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/provisional_site_main.png)

* Press [+] "Add" button to create a new App id. [add image]
* Complete the form.

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/identifier_register.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/identifier_register.png)

* Open XCode project and select Target.
* Write the Bundle Identifier.

**Note**: The Bundle Identifier (App ID + App ID suffix). example: com.gizra.publiceducation.newAppIdSuffix.

## Create a secure Distribution Certificate

* Open Keychain Access in your mac.
* Open preferences.
* Turn off OCSP and CRL options.

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/kaychain_access_preference.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/kaychain_access_preference.png)

* Select in the menu Keychain Access -> Certificate Assistant -> Request a Certificate From a Certificate Authority...

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/request_certificate.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/request_certificate.png)

* Fill User Email Address with the same email information of account iOS Developer.
* Leave CA Email Address: in blank.
* Select "Save to disk" and Let me specify key pair information.

This save a request certificate file in your computer, with the extension .certSigningRequest.

## Add certificate to Provisioning Portal

* Open the [Provisioning Portal.](http://developer.apple.com/ios/manage/overview/)
* Select Certificates.
* Press "Add" button to create a new iOS Certificate.
* Select "App Store and Ad Hoc" in the section Production.

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/add_new_certificate.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/add_new_certificate.png)

* Press Continue to skip the information, because we already request the Certificate.
* Select the request certificate file saved in your computer. example: CertificateSigningRequest.certSigningRequest

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/upload_signing_request.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/upload_signing_request.png)

* Select Continue to generate the certificate and download it.
* Double click the certificate file (*.cer) and this install the certificate.

## (Optional) Backup certificate

* Open Keychain Access.
* Select in the menu File -> Export Items...

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/export_certificate.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/export_certificate.png)

* Save the file (*.p12) on the disk.

**Note**: This file can be use, if need to reinstall the system or do the rest of the process in other computer, without repeat the certificate process.

## Create A Distribution Provisioning Profile

* Open the [Provisioning Portal.](http://developer.apple.com/ios/manage/overview/)
* Select Provision Profiles.
* Press "Add" button to create a new Provisioning Profile.
* Select "App Store" in the section Production.

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/provisioning_profile_form.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/provisioning_profile_form.png)

* Select App ID.

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/provisioning_profile_app_id.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/provisioning_profile_app_id.png)

* Select Certificate (iOS Distribution).

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/provisioning_profile_certificate.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/provisioning_profile_certificate.png)

* Write a name of your profile and generate.
* Download and double click to install the Provisioning Profile.

## Check Code Signing & Build Settings

_Configuration Project:_
* Open XCode and select project and select tab "Build Settings".
* Select in the search filter "All" and "Combined".
* Look for "Deployment" -> "Skip install" and select "Yes".

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/project_skip%20installation.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/project_skip%20installation.png)


_Configuration Target - General:_
* Select the target and tab "General".
* Check out you have define a valid "Bundle Identifier", this have to be App ID defined in the "Create unique App ID" step. **(must include the App ID Suffix)** example: com.gizra.publiceducation.1
* Select Team.

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/project_select_team.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/project_select_team.png)

**Note**: Select the account used to create the certificate.

_Configuration Target - General - App Icons:_
* Source select "Don't use asset catalogs".

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/donot_asset_catalogs.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/donot_asset_catalogs.png)

* Create a new assets catalog.

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/new_assets_catalog.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/new_assets_catalog.png)

* Press the arrow and Drag and Drop the icons of your application.
* Select the new catalog in source.

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/target_select_new_appicon.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/target_select_new_appicon.png)

_Configuration Target - Build Settings:_
* Select target and tab "Build Settings".
* Look for "Code Signing" -> "Code Signing Identify" -> "Release" -> "Any iOS SDK" and select the Certificate generated. (Must be associated to the Provisioning Profile)

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/target_code_signing.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/target_code_signing.png)

* Look for "Code Signing" -> "Provisioning Profile" and select the Provisioning Profile generated.

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/target_build_settings_provisioning_profile.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/target_build_settings_provisioning_profile.png)

* Look for "Deployment" -> "Skip install" and select "No".

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/target_build_settings_skip_install.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/target_build_settings_skip_install.png)

## Create an App in iTunes Connect
* Open the [iTunes Connect](http://itunesconnect.apple.com/) site.
* Select "Manage Your Application"

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/iTunes_Connect_home.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/iTunes_Connect_home.png)

* Select "Add new App"
* Complete the information of the application.

**Note** Must select the **_Bundle ID with the App ID Suffix_** created in "Create unique App ID" step.

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/new%20app%20itunes.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/new%20app%20itunes.png)

## Build and archive the application
* Select in the menu "Product" -> "Scheme" -> "Edit Scheme".

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/edit_scheme.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/edit_scheme.png)

* Select "Archive".
* Select "Build Configuration" to "Release" and press OK button.

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/scheme_archive_configuration.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/scheme_archive_configuration.png)

* Build the application selecting in the menu "Product" -> "Archive".

![https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/build_and_archive_app.png](https://raw.github.com/Gizra/KnowledgeBase/master/assets/images/build_and_archive_app.png)

**Note** This step archive the application and open the "Organizer" tool of XCode.

## Validate and Submit the application
* Select the application archived in the "Organizer" of XCode.
* Press button "Validate...".
* Select credential generated for the application.
* When the validate is complete, the application can be submitted press the "Distribute..." button..
* The state of the validate and submit process could be checked in [iTunes Connect](http://itunesconnect.apple.com/) site.

## Resolve Issues
You can check the official documentation of Apple to solve issues in the build and submit process
https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/Troubleshooting/Troubleshooting.html#//apple_ref/doc/uid/TP40012582-CH5-SW2