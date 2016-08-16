<div class="entry-content">
    <small>webGL을 입문하는 입장에서 가장 큰 어려움은 생소한 용어와 왠지 복잡해보이는 개념의 거부감입니다.<br>
차근차근 기초 용어부터 살짝 들여다 보겠습니다.</small>
    <p></p>
    <hr>
    <h1>1.Triangle</h1>
    <p>3D의 기본개념은 아래와 같은 <strong>작은 삼각형으로 어떠한 형상을 그려내는 것</strong>입니다.<small>일반적인 영화나 게임에서 보이는 3D화면들도 실제로는 작은 Triangle으로 구성된 다각형일 뿐입니다. 각 삼각형은 결국 3개의 꼭지점으로 구성됩니다. 이 꼭지점을 연결한 영역을 삼각형으로 판별할 수 있습니다.</small><br>
        <img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/0012.png" alt="001" width="50%"><img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/0021.png" alt="002" width="50%"><br>
        <small>삼각형에서 꼭지점 1개를 확장하면 2개의 삼각형을 그릴수 있습니다. 이를 이용해 사각형을 그리거나 꼭지점을 더 많이 추가하여 아래와 같은 다각형 또한 그릴 수 있습니다.</small><br>
        <img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/006.gif" alt="006" width="100%" class="wp-image-338"></p>
    <p><strong>요약 – webGL로 삼각형 그리면 입문이다!</strong></p>
    <hr>
    <h1>2.Vertex &amp; Geometry</h1>
    <p>이때 각각의 꼭지점을 <strong>버텍스(Vertex)</strong>라고 합니다.<br>
        <img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/003.png" alt="003" width="50%"><img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/004.png" alt="004" width="50%"><br> 버텍스를 연결한 영역(삼각형으로 이루어진 영역)을 <strong>지오메트리(Geometry)</strong>라고 합니다.<br>
        <small>우리가 많이 사용하는 HTML로 생각해보면 Dom Model은 Rect(사각형) Geometry만을 이용하고 있다고 볼 수 있습니다.</small></p>
    <p><strong>요약 – Vertex를 잘구성해서 원하는 모양(Geometry)를 만든다!</strong></p>
    <hr>
    <h1>3.Buffer와 Shader</h1>
    <p>webGL은 이 Geometry를 고속으로 처리하기 위해 <strong>GPU를 통해서 렌더링</strong>을 하게 됩니다.<br>
        <small>(렌더링 : 1장의 이미지를 그려내는 과정)</small><br> 결국 삼각형 정보를 GPU에 업로드 하게 되는데 GPU 올라간 Vertex정보를 <strong>Vertex Buffer</strong>라고 합니다. GPU에 올라간 Vertex Buffer는 <strong>Shader</strong>라는 작은 프로그램을 통해서 연산되고 실제로 그려지게 됩니다.</p>
    <p>Shader는 <strong>Vertex Shader</strong>와 <strong>Fragment Shader</strong>라는 두가지 형태로 구분되며<br> Vertex -&gt; Fragment로 순차 실행 됩니다. </p>
    <hr>
    <li><strong>Vertex Shader</strong></li>
    <p><img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/004-150x150.png" alt="004" width="150" height="150" class="alignright size-thumbnail wp-image-335"><small>각각의 꼭지점을 어떻게 연결할 것인가에 대한 연산을 담당합니다.<br>
즉 Geometry를 결정하게 됩니다. 지오메트리를 결정하는 과정에서 아래와 같은 여러 처리를 동반 할 수도 있습니다.</small></p><small>
<li>Position(x,y,z)처리</li>
<li>rotation등의 처리</li>
<li>..기타 등등</li>
</small>
    <p><small></small></p>
    <div style="clear:both;display:block"></div>
    <hr>
    <li><strong>Fragment Shader</strong></li>
    <p><small>Vertex Shader에서 확정된 Geometry에 색을 어떻게 채워 나갈 것 인가에 대해서 결정하게 됩니다.<br>
색을 채워 나가는 방식은 크게 2가지가 있습니다.<br>
<img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/007-150x150.png" alt="컬러링" width="150" height="150" class="alignleft size-thumbnail "><img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/008-150x150.png" alt="텍스쳐링" width="150" height="150" class="alignleft size-thumbnail "><br>
A.	컬러링 – 직접적인 색상지정<br>
B.	텍스쳐링 – 이미지 파일을 Geometry에 그리는 방법</small></p>
    <div style="clear:both;display:block"></div>
    <p>두가지를 한꺼번에 활용하여 텍스쳐 처리된 픽셀에 컬러를 더할 수도 있습니다. Fragment를 잘 활용할 수 있게되면 포토샵에서 보던 합성효과들을 구현할 수도 있게됩니다.</p>
    <p><strong>요약 – GPU로 정보를 보내야하며 Shader를 통해서 연산한다! </strong></p>
    <hr>
    <p>3D 프로세싱을 가장작은 단위의 이해인 Triangle과 Triangle을 그리기위해 알아야할 기초 용어들을 알아 보았습니다.<br>
        <strong>Vertex , Geometry, Buffer, Vertex Shader, Fragment Shader</strong> 5개군요.<br>
        <small>webGL을 통해서 무언가를 시도하기 위한 가장 기본 개념인 셈이죠.<br>
앞으로 이 개념을 조금 면밀히 살펴보면서 webGL에 대한 이해를 서서히 높여보도록 하겠습니다. </small></p>
    <hr>
    <strong>Today summary</strong>
    <p></p>
    <p><img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/005.png" alt="005" width="100%"><br> 1. 삼각형 정보를 JavaScript로 구성하고<br> 2. webGL API를 통하여 GPU로 정보를 보내고<br> 3. GPU에서 Shader를 통해서 결과를 출력한다 </p>
    <div class="addthis_toolbox addthis_default_style addthis_32x32_style" addthis:url="http://www.bswebgl.com/?p=326" addthis:title="WebGL Study 001 – WebGL 프로그래밍의 기본 개념이해 "><a class="addthis_button_facebook at300b" title="Facebook" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(59, 89, 152);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="Facebook" alt="Facebook" style="width: 32px; height: 32px;" class="at-icon at-icon-facebook"><g><path d="M22 5.16c-.406-.054-1.806-.16-3.43-.16-3.4 0-5.733 1.825-5.733 5.17v2.882H9v3.913h3.837V27h4.604V16.965h3.823l.587-3.913h-4.41v-2.5c0-1.123.347-1.903 2.198-1.903H22V5.16z" fill-rule="evenodd"></path></g></svg></span></a><a class="addthis_button_twitter at300b" title="Tweet" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(29, 161, 242);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="Twitter" alt="Twitter" style="width: 32px; height: 32px;" class="at-icon at-icon-twitter"><g><path d="M27.996 10.116c-.81.36-1.68.602-2.592.71a4.526 4.526 0 0 0 1.984-2.496 9.037 9.037 0 0 1-2.866 1.095 4.513 4.513 0 0 0-7.69 4.116 12.81 12.81 0 0 1-9.3-4.715 4.49 4.49 0 0 0-.612 2.27 4.51 4.51 0 0 0 2.008 3.755 4.495 4.495 0 0 1-2.044-.564v.057a4.515 4.515 0 0 0 3.62 4.425 4.52 4.52 0 0 1-2.04.077 4.517 4.517 0 0 0 4.217 3.134 9.055 9.055 0 0 1-5.604 1.93A9.18 9.18 0 0 1 6 23.85a12.773 12.773 0 0 0 6.918 2.027c8.3 0 12.84-6.876 12.84-12.84 0-.195-.005-.39-.014-.583a9.172 9.172 0 0 0 2.252-2.336" fill-rule="evenodd"></path></g></svg></span></a><a class="addthis_button_email at300b" target="_blank" title="이메일" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(132, 132, 132);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="Email" alt="Email" style="width: 32px; height: 32px;" class="at-icon at-icon-email"><g><g fill-rule="evenodd"></g><path d="M27 22.757c0 1.24-.988 2.243-2.19 2.243H7.19C5.98 25 5 23.994 5 22.757V13.67c0-.556.39-.773.855-.496l8.78 5.238c.782.467 1.95.467 2.73 0l8.78-5.238c.472-.28.855-.063.855.495v9.087z"></path><path d="M27 9.243C27 8.006 26.02 7 24.81 7H7.19C5.988 7 5 8.004 5 9.243v.465c0 .554.385 1.232.857 1.514l9.61 5.733c.267.16.8.16 1.067 0l9.61-5.733c.473-.283.856-.96.856-1.514v-.465z"></path></g></svg></span></a><a class="addthis_button_pinterest_share at300b" target="_blank" title="Pinterest" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(203, 32, 39);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="Pinterest" alt="Pinterest" style="width: 32px; height: 32px;" class="at-icon at-icon-pinterest_share"><g><path d="M7 13.252c0 1.81.772 4.45 2.895 5.045.074.014.178.04.252.04.49 0 .772-1.27.772-1.63 0-.428-1.174-1.34-1.174-3.123 0-3.705 3.028-6.33 6.947-6.33 3.37 0 5.863 1.782 5.863 5.058 0 2.446-1.054 7.035-4.468 7.035-1.232 0-2.286-.83-2.286-2.018 0-1.742 1.307-3.43 1.307-5.225 0-1.092-.67-1.977-1.916-1.977-1.692 0-2.732 1.77-2.732 3.165 0 .774.104 1.63.476 2.336-.683 2.736-2.08 6.814-2.08 9.633 0 .87.135 1.728.224 2.6l.134.137.207-.07c2.494-3.178 2.405-3.8 3.533-7.96.61 1.077 2.182 1.658 3.43 1.658 5.254 0 7.614-4.77 7.614-9.067C26 7.987 21.755 5 17.094 5 12.017 5 7 8.15 7 13.252z" fill-rule="evenodd"></path></g></svg></span></a><a class="addthis_button_compact at300m" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(255, 101, 80);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="More" alt="More" style="width: 32px; height: 32px;" class="at-icon at-icon-addthis"><g><path d="M18 14V8h-4v6H8v4h6v6h4v-6h6v-4h-6z" fill-rule="evenodd"></path></g></svg></span></a><a class="addthis_counter addthis_bubble_style" href="#" style="display: inline-block;"><a class="addthis_button_expanded" target="_blank" title="더 보기" href="#">13</a><a class="atc_s addthis_button_compact"><span></span></a></a>
        <div class="atclear"></div>
    </div>
</div>
