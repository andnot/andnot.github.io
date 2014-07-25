---
layout: page
title: Wiki
---
<div class="wiki">
    
</div>
<script type="text/javascript">
    $(document).ready(function(){
        $('#content a').each(function(index,element){
            var href = $(this).attr('href');
            if(href.indexOf('#') == 0){
            }else if ( href.indexOf('/') == 0 || href.toLowerCase().indexOf('andnot.github.io/')>-1 ){
                $(this).attr('target','_blank');
            }else{
                $(this).attr('target','_blank');
                $(this).addClass('external');
            }
        });
        $('body').delegate('h2','click',function(e){
            e.preventDefault();
            $(this).next('ul').toggle();
        });
    });
</script>

