---
layout: post
title: Sharepoint 2013 Farklı Kullanıcı ile Oturum Aç (Sign in Different User) Menüsü
categories:
- blog
- sharepoint
---

> Dosyanın Yolu:

`C:\Program Files\Common Files\microsoft shared\Web ServerExtensions\15\TEMPLATE\CONTROLTEMPLATES\welcome.ascx`


> Bu Dosyanın içerisine alan ekliyoruz:

`<SharePoint:MenuItemTemplate runat="server" ID="ID_LoginAsDifferentUser"
  Text="<%$Resources:wss,personalactions_loginasdifferentuser%>"
  Description="<%$Resources:wss,personalactions_loginasdifferentuserdescription%>"
  MenuGroupId="100"
  Sequence="100"
  UseShortId="true"
  />`


 *Kayıt edip kapatıyoruz. Bu kadar..*
