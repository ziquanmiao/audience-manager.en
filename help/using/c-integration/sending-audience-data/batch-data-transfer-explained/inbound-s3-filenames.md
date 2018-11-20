---
description: Describes the required fields, syntax, naming conventions and file sizes you need to follow when sending data to Audience Manager. Set the names and sizes of your files according to these specifications when you send data to an Audience Manager / Amazon S3 directory.
seo-description: Describes the required fields, syntax, naming conventions and file sizes you need to follow when sending data to Audience Manager. Set the names and sizes of your files according to these specifications when you send data to an Audience Manager / Amazon S3 directory.
seo-title: Amazon S3 Name and File Size Requirements for Inbound Data Files
solution: Audience Manager
title: Amazon S3 Name and File Size Requirements for Inbound Data Files
uuid: 3692a122-6ad5-468c-934e-53067bd8cf71
index: y
internal: n
snippet: y
---

# Amazon S3 Name and File Size Requirements for Inbound Data Files{#amazon-s-name-and-file-size-requirements-for-inbound-data-files}

Describes the required fields, syntax, naming conventions and file sizes you need to follow when sending data to Audience Manager. Set the names and sizes of your files according to these specifications when you send data to an Audience Manager / Amazon S3 directory.

Contents:

* [File Name Syntax](../../../c-integration/sending-audience-data/batch-data-transfer-explained/inbound-s3-filenames.md#section_A572A6BC39D34462BE9CEA184FE9E556) 
* [File Name Examples](../../../c-integration/sending-audience-data/batch-data-transfer-explained/inbound-s3-filenames.md#section_310A0F2330FD4E109F54227736BFEA89) 
* [Accepted File Sizes](../../../c-integration/sending-audience-data/batch-data-transfer-explained/inbound-s3-filenames.md#section_2E2BE21030A34BA1AE67288F333780A0)

>[!NOTE]
>
>The text styles ( `monospaced text`, *italics*, brackets [ ] ( ), etc.) in this document indicate code elements and options. See [Style Conventions for Code and Text Elements](../../../reference/code-style-elements.md#reference_59D0BD0EDB424A65853460D91CCA35D9) for more information.

## File Name Syntax {#section_A572A6BC39D34462BE9CEA184FE9E556}

S3 file names contain the following required and optional elements:

* **S3 prefix: ** `s3n:// *`AWS_directory`*/ *`partner_name`*/date= *`yyyy-mm-dd`*/` 

* **File name elements:** `ftp_dpm_ *`DPID`*[ *`_DPID_TARGET_DATA_OWNER`*]_ *`TIMESTAMP`*(.sync|.overwrite)[. *`SPLIT_NUMBER`*][.gz]`

>[!NOTE] {importance="high"}
>
>[!DNL Audience Manager] only processes ASCII and UTF-8 encoded files.

**Name Elements**

The table defines the elements in an S3 file name.

<table id="table_455D174BAB9B494D973DA1023F22B962"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Name Element </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> <span class="varname"> AWS_directory</span> </span> </p> </td> 
   <td colname="col2"> <p>The path to and name of your Amazon S3 bucket. Contact your Account Manager for your S3 directory name, path, and credentials. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph">date=<span class="varname"> yyyy-mm-dd</span></span> </p> </td> 
   <td colname="col2"> <p>A timestamp (based on UTC time) of when you send the files to your S3 bucket. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> <span class="varname"> DPID</span> </span> </p> </td> 
   <td colname="col2"> <p>The <span class="term"> Data Provider ID</span> (DPID) is an identifier that tells <span class="keyword"> Audience Manager</span> if a data file contains your own user IDs or Android or iOS IDs. Accepts the following options: </p> <p> <b>Data Partner ID</b> </p> <p>This is a unique ID Audience Manager assigns to your company or organization. Use this assigned ID in a file name when sending in data that contains your own user IDs. For example, <span class="codeph">...ftp_dpm_21_123456789.sync</span> tells <span class="keyword"> Audience Manager</span> that a partner with ID 21 sent the file and it contains user IDs assigned by that partner. </p> <p> <b>Android IDs (GAID)</b> </p> <p> Use ID 20914 as the DPID in a data file name if the file contains Android IDs. When you use ID 20914 as the DPID, you still need to identify your company to <span class="keyword"> Audience Manager</span>. This means the file name must use the <span class="codeph"><span class="varname"> _DPID_TARGET_DATA_OWNER</span></span> parameter to hold your company ID. For example, say you're passing in files with Android IDs and your Data Provider ID is 21. In this case, the file name would look like <span class="codeph">...ftp_dpm_20914_21_123456789.sync</span>. This tells <span class="keyword"> Audience Manager</span> the file contains Android IDs and is from a partner identified by ID 21. </p> <p> <b>iOS IDs (IDFA)</b> </p> <p> Use ID 20915 as the DPID in a data file name if the file contains iOS IDs. When you use ID 20915 as the DPID, you still need to identify your company to <span class="keyword"> Audience Manager</span>. This means the file name must use the <span class="codeph"><span class="varname"> _DPID_TARGET_DATA_OWNER</span></span> parameter to hold your company ID. For example, say you're passing in files with Android IDs and your Data Provider ID is 21. In this case, the file name would look like <span class="codeph">...ftp_dpm_20915_21_123456789.sync</span>. This tells <span class="keyword"> Audience Manager</span> the file contains iOS IDs and is from a partner identified by ID 21. </p> 
    <draft-comment> 
     <ul id="ul_818EB3EB2E5543F0B048BCEBB6699562"> 
      <li id="li_ED6B13CB49794F6BA3DB6D807F788BAF"> <b>Data Partner ID:</b> This is a unique ID Audience Manager assigns to your company or organization. Use this assigned ID in a file name when sending in data that contains your own user IDs. For example, <span class="codeph">...ftp_dpm_21_123456789.sync</span> tells <span class="keyword"> Audience Manager</span> that a partner with ID 21 sent the file and it contains user IDs assigned by that partner. </li> 
      <li id="li_1955911BA11F4F458227B77F383F25A3"> <b>Android IDs (GAID):</b> Use ID 20914 in a data file name if it contains Android ID. For example, <span class="codeph">...ftp_dpm_20914_21_123456789.sync</span> tells <span class="keyword"> Audience Manager</span> that the data file contains Android IDs only. Note, the ID 21 </li> 
      <li id="li_54E7734C121646AF82095806DD1AED61"> <b>iOS IDs (IDFA):</b> Use ID 20915 in a data file name if it contains iOS IDs. For example, <span class="codeph">...ftp_dpm_20915_123456789.sync</span> tells <span class="keyword"> Audience Manager</span> that the data file contains iOS IDs only. </li> 
     </ul> 
    </draft-comment> <p> <p>Note:  Do not mix ID types in your data files. For example, if your file name includes the Android identifier, don't put iOS IDs or your own IDs in the data file. </p> </p> <p>See also the <span class="codeph"><span class="varname"> _DPID_TARGET_DATA_OWNER</span></span> entry below. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> <span class="varname"> _DPID_TARGET_DATA_OWNER</span> </span> </p> </td> 
   <td colname="col2"> <p>A placeholder for an ID. For example, you could set it to your <span class="keyword"> Audience Manager</span> ID if you set the DPID to a data source ID or an Android or iOS ID. This lets <span class="keyword"> Audience Manager</span> link the file data back to your organization. </p> <p>For example: </p> 
    <ul id="ul_55EBBCB11F2B4A858AEFBFA1CD99E286"> 
     <li id="li_3404428F4E3D49A5AB6EDF56310D923F"> <span class="codeph">...ftp_dpm_33_21_1234567890.sync</span> shows a partner with ID 21 has sent in data from a data source that uses ID 33. </li> 
     <li id="li_CF8D5AF678764E9984A088FD5D7BBFB6"> <span class="codeph">...ftp_dpm_20914_21_1234567890.sync</span> shows a partner with ID 21 has sent in data that contains Android IDs. </li> 
     <li id="li_3D73168391D7443BADDF27153090274D"> <span class="codeph">...ftp_dpm_20915_21_1234567890.sync</span> shows a partner with ID 21 has sent in data that contains iOS IDs. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> <span class="varname"> parnter_name</span> </span> </p> </td> 
   <td colname="col2"> <p>The company or organization name you use in <span class="keyword"> Audience Manager</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> <span class="varname"> TIMESTAMP</span> </span> </p> </td> 
   <td colname="col2"> <p>A 10-digit, UTC UNIX timestamp in seconds. The timestamp helps make each file name unique. </p> 
    <draft-comment> 
     <p> <p>Note:  Audience Manager does not use the timestamp during processing of inbound files. The timestamp in the filename has been deprecated in Audience Manager but is still required for backwards compatibility. </p> </p> 
    </draft-comment> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> (.sync|.overwrite)</span> </p> </td> 
   <td colname="col2"> <p>Synchronization options that include: </p> <p> 
     <ul id="ul_DAAF61EC636C4456BECDDC34C3F86E83"> 
      <li id="li_6EC6DE442B4546AA9F4F800D65C8A4EC"> <span class="codeph"> sync</span>: Normal scenario when third-party data providers send traits on a per-user basis to be added or removed in the Audience Manager system. </li> 
      <li id="li_8FE8430C2C004F87835D55231A0D99C9"> <span class="codeph"> overwrite</span>: Lets data providers send a list of traits on a per-user basis that should overwrite all of this user's existing third-party traits for this data provider in the Audience Manager. You do not need to include all of your users in an overwrite file. Include only those users that you want to change. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph">[<span class="varname"> SPLIT_NUMBER</span>]</span> </p> </td> 
   <td colname="col2"> <p>An integer. Used when you split large files into multiple parts to improve processing times. The number indicates which part of the original file you're sending in. </p> <p>For efficient file processing, split your data files as indicated: </p> 
    <ul id="ul_E9446C5CA42649658093904D49D4369C"> 
     <li id="li_B275708DFE3F49E29EFAE6B838429E39">Uncompressed: 1 GB </li> 
     <li id="li_A9638EB46ED14E0680B6575D5457E32F">Compressed: 200-300 MB </li> 
    </ul> <p>See the first 2 <a href="../../../c-integration/sending-audience-data/batch-data-transfer-explained/inbound-s3-filenames.md#section_310A0F2330FD4E109F54227736BFEA89"> file name examples</a> below. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> [.gz]</span> </p> </td> 
   <td colname="col2"> <p>When sending files to Amazon S3, use gzip compression only. When compressed, these files get the <span class="codeph"> .gz</span> extension. Do not use .zip compression. </p> <p>Compressed files must be 1 GB or smaller. If your files files are larger, please talk to Customer Care. Although Audience Manager can handle large files, we may be able to help you reduce the size of your files and make data transfers more efficient. See <a href="../../../c-integration/sending-audience-data/batch-data-transfer-explained/inbound-file-compression.md#concept_7D6FA8BA759143EFBEDB16589BF6EC40"> File Compression for Inbound Data Transfer Files</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## File Name Examples {#section_310A0F2330FD4E109F54227736BFEA89}

The following examples show properly formatted file names. Your file names could look similar.

<ul class="simplelist"> 
 <li> <span class="codeph"> s3n://&lt;AWS_Bucket&gt;/&lt;partner_name&gt;/date=2016-05-09/ftp_dpm_478_1366545717.sync.1.gz</span> </li> 
 <li> <span class="codeph"> s3n://&lt;AWS_Bucket&gt;/&lt;partner_name&gt;/date=2016-05-09/ftp_dpm_478_1366545717.sync.2.gz</span> </li> 
 <li> <span class="codeph"> s3n://&lt;AWS_Bucket&gt;/&lt;partner_name&gt;/date=2016-05-09/ftp_dpm_478_1366545717.sync</span> </li> 
 <li> <span class="codeph"> s3n://&lt;AWS_Bucket&gt;/&lt;partner_name&gt;/date=2016-05-09/ftp_dpm_478_567_1366545717.sync.gz</span> </li> 
 <li> <span class="codeph"> s3n://&lt;AWS_Bucket&gt;/&lt;partner_name&gt;/date=2016-05-09/ftp_dpm_478_1366545717.overwrite</span> </li> 
 <li> <span class="codeph"></span> </li> 
</ul>

You can [download](https://marketing.adobe.com/resources/help/en_US/aam/downloads/ftp_dpm_1234_1445374061.overwrite) the sample file if you want additional examples. This file has been saved with the `.overwrite` file extension. Open it with a simple text editor.

## Accepted File Sizes {#section_2E2BE21030A34BA1AE67288F333780A0}

Consider the figures below for fastest/earliest processing of your files as well as for file size limitations when you send data to an [!DNL Audience Manager] / Amazon S3 directory.  

<table id="table_59FCC63806684DF8BE54A1EAF224A234"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> File Type </th> 
   <th colname="col2" class="entry"> Optimal Size </th> 
   <th colname="col3" class="entry"> Maximum Size </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><b>Compressed</b> </td> 
   <td colname="col2"> <p>200-300 MB </p> </td> 
   <td colname="col3"> <p>1 GB </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Uncompressed</b> </td> 
   <td colname="col2"> <p>1 GB </p> </td> 
   <td colname="col3"> <p>5 GB </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>The inbound data validation process will mark empty files as invalid and will not process them.

>[!MORE_LIKE_THIS]
>
>* [FTP Name Requirements for Inbound Data Files](../../../c-integration/sending-audience-data/batch-data-transfer-explained/inbound-ftp-filenames.md#concept_D34898442363415DBF75CEBFC2E86997)