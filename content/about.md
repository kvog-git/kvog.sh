+++
title = 'About'
+++

My name is Hunter. I'm a hobbyist multimedia programmer from Minnesota.

I can be reached at <span id="my-email">(hover to reveal email)</span>.
<script>
    let d = document.getElementById('my-email');
    d.addEventListener('mouseenter', () => {
        let address = atob('aHVudGVyQGt2b2cuc2g=');
        d.innerHTML = `<a href="mailto:${address}">${address}</a>`;
    });
</script>

This website's source code can be downloaded here: [master.tar.gz](https://github.com/kvog-git/kvog.sh/archive/refs/heads/master.tar.gz).
