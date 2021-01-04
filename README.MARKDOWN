*Our blog can be approach.*

### Content

Mostly about random stuff I've been thinking important to keep, nonetheless filled with an easy tutorial.

### Feature
 
`_Posts` folder was a directory for writed article `{year}-{month}-{day}-{title-name}.md` with metadata :

```
---
title:  "{year}-{month}-{day}-{title-name}"
comments: true
---

{blog-content}
```

This part a script for `disqus.com` comment section.

```
<div id="disqus_thread"></div>
<script>
    /**
    *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
    *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables    */
    /*
    var disqus_config = function () {
    this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
    this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    */
    (function() { // DON'T EDIT BELOW THIS LINE
    var d = document, s = d.createElement('script');
    s.src = 'https://bahasalien.disqus.com/embed.js';
    s.setAttribute('data-timestamp', +new Date());
    (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
```
 
We trying not using HTML in such a beautifully way, taking attention while your contribution has been arrive.
 
|                   |                                                                                        |
| -                 | -                                                                                      |
| Image             | `<img src="https://raw.githubusercontent.com/.../{filename.jpg}" alt="{tag}">`         |
| Audio             | Contributor needed!                                                                    |
| Video             | Contributor needed!                                                                    |
| Data/Iframe       | Contributor needed!                                                                    |

<marquee behavior="alternate" bgColor="black" style="border:solid" direction="right" scrollamount="1"><b>Markdown Lover's!</b></marquee>

### Structure

Index file was a `README.md`, markdown automatically translated file to HTML.

```structure
.
├── .github/
|   └── workflows
|   |   └── dynamic-readme.yml
├── _assets/
|   └── img/
|   |   ├── [name-folder]/
|   |   |    ├── [name-file].jpg
|   |   |    └── []
|   |   └── []
├── _drafts/
|   ├── [year-month-day-title].md
|   └── []
├── _posts/
|   ├── [year-month-day-title].md
|   └── []
├── []
└── README.md
```

### License

```license
            DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
                    Version 2, December 2004

 Copyright (C) 2021 M. Syamsir Alam (syamsiralam.id@gmail.com) and Contributor

 Everyone is permitted to copy and distribute verbatim or modified
 copies of this license document, and changing it is allowed as long
 as the name is changed.

            DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
   TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION

  0. You just DO WHAT THE FUCK YOU WANT TO.
  ```
