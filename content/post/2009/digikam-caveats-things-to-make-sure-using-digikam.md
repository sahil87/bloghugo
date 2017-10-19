---
title: Digikam Caveats - things to make sure using Digikam
author: Sahil Ahuja
categories: [blog]
tags:
  - backup
  - digikam
  - linux
  - photography
date: 2009-11-14 19:19:03
---

I have been bitten. And so I post this in the hope that some needy soul finds this before he/she/it gets bitten too.

**Problem**: [Digikam](http://www.digikam.org/) saves image tags (ratings/captions that you spend hours editing) in its internal database. When you switch to a newer linux version, lose this information - unless you are careful enough to copy over the digikam.db4 file - which I was. The second problem is that if you move around or copy your files using a file browser, you lose this information ( !!!! ), and digikam doesn't allow copy of albums (!!).

**Solution**:

1.  Specify the location of your digikam.db4 file as the root directory of you photo library. This way, when you move your library, you have the digikam database with you.This can be configured through digikam Configuration &gt; Collections.
2.  The most important step (which digikam should have made default according to the [Principle of least astonishment](http://en.wikipedia.org/wiki/Principle_of_least_astonishment))

    *   Enable the all options starting with "Save" in digikam Configuration &gt; Metadata. This would save all tags, ratings, captions and copyright information directly in the image instead of relying on digikam database for it.
![digikam-metadata-setting](/images/2009/digikam-metadata-setting.jpg?w=300 "digikam-metadata-setting")
    *   Add author and copyright information in digikam Configuration &gt; Identity. I put the following there:
        *   **Author:** Sahil Ahuja
        *   **Credit:** Sahil Ahuja
        *   **Source:** http://sahilahuja.wordpress.com
        *   **Copyright:** [CC BY 3.0](http://creativecommons.org/licenses/by/3.0/)
![digikam-identity-setting](/images/2009/digikam-identity-setting.jpg?w=300 "digikam-identity-setting")
These steps will ensure that from now on all you files get **properly** tagged, the way you mean them to be.
**What about the images I have already tagged, captioned and rated?**

After these setting are applied, digikam enforces them only for images you write to from now onwards. For images that are already in your library, we need a write operation on them to embed the metadata into the files.

This can can be done by creating a custom search that matches all possible ratings one by one, and right clicking and assigning the same rating again. Do the same for all tags too. And now all your metadata should get embedded in the file. Voila!

![digikam-customSearch-rating](/images/2009/digikam-customsearch-rating.jpg?w=300 "digikam-customSearch-rating")
