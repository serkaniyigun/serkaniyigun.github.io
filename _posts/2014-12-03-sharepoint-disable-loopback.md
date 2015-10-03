---
layout: post
title: Sharepoint Disable Loopbackcheck disable with Powershell
categories:
- blog
- sharepoint
---


İlk Sharepoint kurulumunuzdan sonra giriş yaptığınız da sürekli olarak sizden kullanıcı kimlik bilgileri isteniyorsa Loopback check kapatmak zorundasınız. En temiz ve kısa yol Powershell.P

######PowerShell Üzerinden Gerçekleştirmek için

----

`New-ItemProperty HKLM:\System\CurrentControlSet\Control\Lsa -Name "DisableLoopbackCheck" -value "1" -PropertyType dword`

----
Sunucuyu tekrar başlatmak gereklidir..
