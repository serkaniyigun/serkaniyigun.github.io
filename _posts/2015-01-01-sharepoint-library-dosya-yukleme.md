---
layout: post
title: Sharepoint Library üzerine PowerShell ile Dosya Yükleme
categories:
- blog
- sharepoint
---


`[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint")
if((Get-PSSnapin | Where {$_.Name -eq "Microsoft.SharePoint.PowerShell"}) -eq $null) {
     Add-PSSnapin Microsoft.SharePoint.PowerShell;
 }`

`#Site Collection where you want to upload files
$siteCollUrl = "http://site"`

`#Document Library where you want to upload files`


`$libraryName = "Library"`

`#Physical/Network location of files
$reportFilesLocation  = "C:\location of files"`

`$spSourceWeb = Get-SPWeb $siteCollUrl;
$spSourceList = $spSourceWeb.Lists[$libraryName];`

`if($spSourceList -eq $null)
{
	Write-Host "The Library $libraryName could not be found."
	return;
}`

`$files = ([System.IO.DirectoryInfo] (Get-Item $reportFilesLocation)).GetFiles()
foreach($file in $files)`
`{
	#Open file`

    $fileStream = ([System.IO.FileInfo] (Get-Item $file.FullName)).OpenRead()

    #Add file
	$folder =  $spSourceWeb.getfolder($libraryName)`

    Write-Host "Copying file $file to $libraryName..."
	$spFile = $folder.Files.Add($folder.Url + "/" + $file.Name, [System.IO.Stream]$fileStream, $true)`

    #Close file stream
	$fileStream.Close();

    }
`$spSourceWeb.dispose();
Write-Host "Files have been uploaded to $libraryName."`
