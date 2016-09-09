
---
title: Custom Web Themes in AD FS
description:
author: billmath
manager: femila
ms.date: 08/31/2016
ms.topic: article
ms.prod: windows-server-threshold
ms.service: active-directory
ms.technology: active-directory-federation-services
---
# Custom Web Themes in AD FS 

>Applies To: Windows Server 2016, Windows Server 2012 R2

The theme that is shipped out\-of\-the\-box is called Default. You can export the default theme and use it so that you can start quickly. You can customize the appearance and behavior, which includes the layout by modifying the .css file, import and apply this new theme, and then you can use the customized appearance and behavior. Using the .css file also makes it easier to work with your web designers.  
  
The following cmdlet creates a custom web theme, which duplicates the default web theme.  
  
  
`New-AdfsWebTheme –Name custom –SourceName default ` 

  
You can modify the .css file and configure the new web theme by using the new .css file. To export a web theme, use the following cmdlet.  
  

    Export-AdfsWebTheme –Name default –DirectoryPath c:\theme  

  
To apply the .css file to the new theme, use the following cmdlet.  
  

    Set-AdfsWebTheme –TargetName custom –StyleSheet @{path=”c:\NewTheme.css”}  
  
  
The following cmdlet creates a custom web theme from a new style sheet.  
  
  
`New-AdfsWebTheme –Name custom –StyleSheet @{path=”c:\NewTheme.css”} –RTLStyleSheetPath c:\NewRtlTheme.css ` 
  
  
  
To apply the custom web theme to AD FS, use the following cmdlet.  
  

`Set-AdfsWebConfig -ActiveThemeName custom`  

  
To add JavaScript to AD FS, use the following cmdlet.  
  
 
    Set-AdfsWebTheme -TargetName custom -AdditionalFileResource @{Uri=’ /adfs/portal/script/onload.js’;path="D:\inetpub\adfsassets\script\onload.js"}  


## Additional references 
[AD FS User Sign-in Customization](AD-FS-user-sign-in-customization.md)  