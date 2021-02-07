---
title:  "05-January-2021"
description: "Feature Blog"
comments: true
---

*Audio*
---
<audio controls>
  <source src="https://raw.githubusercontent.com/1995re/1995re.github.io/main/data/aud/untitled.mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>

*Video*
---
<video controls>
  <source src="https://raw.githubusercontent.com/1995re/1995re.github.io/main/data/vid/000032BoskoAndHoneyLt.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

*Data*
---
<div id='table-container'></div>

<script type="text/javascript" src="https://raw.githubusercontent.com/derekeder/csv-to-html-table/master/js/jquery.min.js"></script>
<script type="text/javascript" src="https://raw.githubusercontent.com/derekeder/csv-to-html-table/master/js/bootstrap.min.js"></script>
<script type="text/javascript" src="https://raw.githubusercontent.com/derekeder/csv-to-html-table/master/js/jquery.csv.min.js"></script>
<script type="text/javascript" src="https://raw.githubusercontent.com/derekeder/csv-to-html-table/master/js/jquery.dataTables.min.js"></script>
<script type="text/javascript" src="https://raw.githubusercontent.com/derekeder/csv-to-html-table/master/js/dataTables.bootstrap.js"></script>
<script type="text/javascript" src="https://raw.githubusercontent.com/derekeder/csv-to-html-table/master/js/csv_to_html_table.js"></script>

<script>

  //my custom function that creates a hyperlink
  function format_link(link){
    if (link)
      return "<a href='" + link + "' target='_blank'>" + link + "</a>";
    else
      return "";
  }

  //initializing the table
  CsvToHtmlTable.init({
    csv_path: '../data/testdata.csv', 
    element: 'table-container', 
    allow_download: false,
    datatables_options: {"paging": false},
  });
</script>

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
