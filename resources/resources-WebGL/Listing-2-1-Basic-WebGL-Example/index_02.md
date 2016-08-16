<div class="entry-content">
    <strong>1. Context &amp; Initialize</strong><br> webGL은 많은 분들이 이용하고 있는 Canvas태그 Context의 한 종류입니다.
    <p></p>
    <p><small>일반적인 캔버스라고 하면</small></p>
    <!-- Crayon Syntax Highlighter v2.6.9 -->

    <div id="crayon-57b2a4e5a4467936106158" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">

        <div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">Canvas 2D Context</span>
            <div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;">
                <div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-plain-button" title="일반 코드 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-copy-button" title="복사">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-popup-button" title="새 창에서 보기">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div><span class="crayon-language">JavaScript</span></div>
        </div>
        <div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
        <div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">var canvas2D = canvas.getContext(‘2D’) // 2D Context 요청
canvas2D.fillRect() // 전용 API</textarea></div>
        <div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
            <table class="crayon-table">
                <tbody>
                    <tr class="crayon-row">
                        <td class="crayon-nums " data-settings="show">
                            <div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;">
                                <div class="crayon-num" data-line="crayon-57b2a4e5a4467936106158-1" style="height: 15px;">1</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a4467936106158-2" style="height: 15px;">2</div>
                            </div>
                        </td>
                        <td class="crayon-code">
                            <div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;">
                                <div class="crayon-line" id="crayon-57b2a4e5a4467936106158-1"><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">canvas2D</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">canvas</span><span class="crayon-sy">.</span><span class="crayon-e">getContext</span><span class="crayon-sy">(</span>‘<span class="crayon-cn">2D</span>’<span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-c">// 2D Context 요청</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a4467936106158-2"><span class="crayon-v">canvas2D</span><span class="crayon-sy">.</span><span class="crayon-e">fillRect</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-c">// 전용 API</span></div>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
    <!-- [Format Time: 0.0014 seconds] -->
    <p><small>를 이용해서 canvas2D 전용 API를 사용하게 됩니다. </small></p>
    <p><small><strong>webGL도 동일한 방식으로 webGL API를 사용할 수 있는 컨텍스트를 얻을 수 있습니다.</strong></small></p>
    <!-- Crayon Syntax Highlighter v2.6.9 -->

    <div id="crayon-57b2a4e5a4477599429122" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">

        <div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">Canvas WebGL Context</span>
            <div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;">
                <div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-plain-button" title="일반 코드 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-copy-button" title="복사">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-popup-button" title="새 창에서 보기">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div><span class="crayon-language">JavaScript</span></div>
        </div>
        <div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
        <div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">var gl = canvas.getContext(‘webgl’) // webgl Context 요청
gl.drawArray() // 전용 API</textarea></div>
        <div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
            <table class="crayon-table">
                <tbody>
                    <tr class="crayon-row">
                        <td class="crayon-nums " data-settings="show">
                            <div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;">
                                <div class="crayon-num" data-line="crayon-57b2a4e5a4477599429122-1" style="height: 15px;">1</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a4477599429122-2" style="height: 15px;">2</div>
                            </div>
                        </td>
                        <td class="crayon-code">
                            <div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;">
                                <div class="crayon-line" id="crayon-57b2a4e5a4477599429122-1"><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">canvas</span><span class="crayon-sy">.</span><span class="crayon-e">getContext</span><span class="crayon-sy">(</span>‘<span class="crayon-i">webgl</span>’<span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-c">// webgl Context 요청</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a4477599429122-2"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">drawArray</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-c">// 전용 API</span></div>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
    <!-- [Format Time: 0.0014 seconds] -->
    <p>유의사항 : <small>webGL의 초기화 Context Key는 브라우저마다 상이합니다. 따라서 다양한 변수를 생각해서 모두 체크해서 webGL Context를 활성화 해야합니다.</small><br> 기쁜소식 : <small>초기화 키 값만 다릅니다. API는 모두 동일!</small></p>
    <hr>
    <small><strong>현존하는 활성화 키값</strong>
<ul>
<li>webgl</li>
<li>experimental-webgl</li>
<li>webkit-3d</li>
<li>moz-webgl</li>
</ul>
</small>
    <p><small>이렇게 4가지 입니다.</small></p>
    <hr> 아래와 같이 순차적인 초기화 코드를 작성할 수도 있습니다.<br>
    <!-- Crayon Syntax Highlighter v2.6.9 -->

    <div id="crayon-57b2a4e5a4481961432971" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">

        <div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">webGL 초기화</span>
            <div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-mixed-highlight" title="Contains Mixed Languages"></span>
                <div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-plain-button" title="일반 코드 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-copy-button" title="복사">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-popup-button" title="새 창에서 보기">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div><span class="crayon-language">JavaScript</span></div>
        </div>
        <div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
        <div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">&lt;body&gt;
&lt;canvas id="glCanvas"&gt;&lt;/canvas&gt;
&lt;script&gt;
    var gl, keys = 'webgl,experimental-webgl,webkit-3d,moz-webgl'.split(','), i = keys.length
    var cvs = document.getElementById('glCanvas')
    while (i--) if (gl = cvs.getContext(keys[i])) break
    if (gl) console.log('webgl 초기화 성공!')
    else console.log('webgl 초기화 실패!')
&lt;/script&gt;
&lt;/body&gt;</textarea></div>
        <div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
            <table class="crayon-table">
                <tbody>
                    <tr class="crayon-row">
                        <td class="crayon-nums " data-settings="show">
                            <div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;">
                                <div class="crayon-num" data-line="crayon-57b2a4e5a4481961432971-1" style="height: 15px;">1</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a4481961432971-2" style="height: 15px;">2</div>
                                <div class="crayon-num" data-line="crayon-57b2a4e5a4481961432971-3" style="height: 15px;">3</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a4481961432971-4" style="height: 30px;">4</div>
                                <div class="crayon-num" data-line="crayon-57b2a4e5a4481961432971-5" style="height: 15px;">5</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a4481961432971-6" style="height: 15px;">6</div>
                                <div class="crayon-num" data-line="crayon-57b2a4e5a4481961432971-7" style="height: 15px;">7</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a4481961432971-8" style="height: 15px;">8</div>
                                <div class="crayon-num" data-line="crayon-57b2a4e5a4481961432971-9" style="height: 15px;">9</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a4481961432971-10" style="height: 15px;">10</div>
                            </div>
                        </td>
                        <td class="crayon-code">
                            <div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;">
                                <div class="crayon-line" id="crayon-57b2a4e5a4481961432971-1"><span class="crayon-o">&lt;</span><span class="crayon-v">body</span><span class="crayon-o">&gt;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a4481961432971-2"><span class="crayon-o">&lt;</span><span class="crayon-e">canvas </span><span class="crayon-e ">id</span><span class="crayon-o">=</span><span class="crayon-s">"glCanvas"</span><span class="crayon-o">&gt;</span><span class="crayon-o">&lt;</span><span class="crayon-o">/</span><span class="crayon-e">canvas</span><span class="crayon-o">&gt;</span></div>
                                <div class="crayon-line" id="crayon-57b2a4e5a4481961432971-3"><span class="crayon-ta">&lt;script&gt;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a4481961432971-4"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-e ">keys</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-s">'webgl,experimental-webgl,webkit-3d,moz-webgl'</span><span class="crayon-sy">.</span><span class="crayon-e">split</span><span class="crayon-sy">(</span><span class="crayon-s">','</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">i</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">keys</span><span class="crayon-sy">.</span><span class="crayon-e">length</span></div>
                                <div class="crayon-line" id="crayon-57b2a4e5a4481961432971-5"><span class="crayon-e">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">cvs</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">document</span><span class="crayon-sy">.</span><span class="crayon-e">getElementById</span><span class="crayon-sy">(</span><span class="crayon-s">'glCanvas'</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a4481961432971-6"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-st">while</span><span class="crayon-h"> </span><span class="crayon-sy">(</span><span class="crayon-v">i</span><span class="crayon-o">--</span><span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-st">if</span><span class="crayon-h"> </span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">cvs</span><span class="crayon-sy">.</span><span class="crayon-e">getContext</span><span class="crayon-sy">(</span><span class="crayon-v">keys</span><span class="crayon-sy">[</span><span class="crayon-v">i</span><span class="crayon-sy">]</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-st">break</span></div>
                                <div class="crayon-line" id="crayon-57b2a4e5a4481961432971-7"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-st">if</span><span class="crayon-h"> </span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-v">console</span><span class="crayon-sy">.</span><span class="crayon-e">log</span><span class="crayon-sy">(</span><span class="crayon-s">'webgl 초기화 성공!'</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a4481961432971-8"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-st">else</span><span class="crayon-h"> </span><span class="crayon-v">console</span><span class="crayon-sy">.</span><span class="crayon-e">log</span><span class="crayon-sy">(</span><span class="crayon-s">'webgl 초기화 실패!'</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a4e5a4481961432971-9"><span class="crayon-ta">&lt;/script&gt;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a4481961432971-10"><span class="crayon-o">&lt;</span><span class="crayon-o">/</span><span class="crayon-v">body</span><span class="crayon-o">&gt;</span></div>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
    <!-- [Format Time: 0.0046 seconds] -->
    <strong>현재 지원 브라우저</strong> : IE11이상, 그 외 모던 브라우저, Safari(요세미티 부터)지원<br>
    <strong>모바일</strong> : 대부분지원 , Safari(iOS 8 부터)지원
    <p></p>
    <hr>
    <strong>2.Render</strong><br>
    <small>콘솔만 찍으면 재미없으니까 webGL을 이용한 간단한 Renderer를 구현해 보겠습니다.<br>
배경색을 계속해서 변경하는 렌더러!</small>
    <!-- Crayon Syntax Highlighter v2.6.9 -->

    <div id="crayon-57b2a4e5a4489288309636" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">

        <div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">render Function</span>
            <div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;">
                <div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-plain-button" title="일반 코드 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-copy-button" title="복사">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-popup-button" title="새 창에서 보기">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div><span class="crayon-language">JavaScript</span></div>
        </div>
        <div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
        <div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">function render(){
    gl.clearColor(Math.random(),Math.random(),Math.random(), 1)
    gl.clear(gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT)
}
setInterval(render,16)</textarea></div>
        <div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
            <table class="crayon-table">
                <tbody>
                    <tr class="crayon-row">
                        <td class="crayon-nums " data-settings="show">
                            <div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;">
                                <div class="crayon-num" data-line="crayon-57b2a4e5a4489288309636-1" style="height: 15px;">1</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a4489288309636-2" style="height: 30px;">2</div>
                                <div class="crayon-num" data-line="crayon-57b2a4e5a4489288309636-3" style="height: 15px;">3</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a4489288309636-4" style="height: 15px;">4</div>
                                <div class="crayon-num" data-line="crayon-57b2a4e5a4489288309636-5" style="height: 15px;">5</div>
                            </div>
                        </td>
                        <td class="crayon-code">
                            <div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;">
                                <div class="crayon-line" id="crayon-57b2a4e5a4489288309636-1"><span class="crayon-t">function</span><span class="crayon-h"> </span><span class="crayon-e">render</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">{</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a4489288309636-2"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">clearColor</span><span class="crayon-sy">(</span><span class="crayon-v">Math</span><span class="crayon-sy">.</span><span class="crayon-e">random</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-v">Math</span><span class="crayon-sy">.</span><span class="crayon-e">random</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-v">Math</span><span class="crayon-sy">.</span><span class="crayon-e">random</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">1</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a4e5a4489288309636-3"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">clear</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">COLOR_BUFFER_BIT</span><span class="crayon-h"> </span><span class="crayon-o">|</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">DEPTH_BUFFER_BIT</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a4489288309636-4"><span class="crayon-sy">}</span></div>
                                <div class="crayon-line" id="crayon-57b2a4e5a4489288309636-5"><span class="crayon-r">setInterval</span><span class="crayon-sy">(</span><span class="crayon-v">render</span><span class="crayon-sy">,</span><span class="crayon-cn">16</span><span class="crayon-sy">)</span></div>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
    <!-- [Format Time: 0.0023 seconds] -->
    <small>앞서 정의한 초기화 코드뒤에 위의 코드만 추가합니다.<br>
16 밀리초로 render 함수를 지속적으로 반복 실행하게 됩니다. <strong>실행을 해보면 색깔이 지속적으로 바뀌는 캔버스를 볼 수 있습니다. </strong><br>
모든 동적 그래픽은 초당 최대 60프레임 까지 그리고 지우기를 반복하며 동적인 화면을 보여주게 됩니다. 마치 영화나 애니메이션의 프레임과 같이 말이죠. 즉 렌더러를 구현한다는 것은 모니터에 프레임을 비춰주는 영사기를 만드는 것과 비슷합니다.<br>
</small><br>
    <iframe src="/blog/index2.html" width="100%" height="300" scrolling="no"></iframe>
    <p></p>
    <hr>
    <strong>Render 함수의 코드를 살펴봅시다. </strong>
    <!-- Crayon Syntax Highlighter v2.6.9 -->

    <div id="crayon-57b2a4e5a4492639824482" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">

        <div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">gl.clearColor</span>
            <div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;">
                <div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-plain-button" title="일반 코드 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-copy-button" title="복사">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-popup-button" title="새 창에서 보기">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div><span class="crayon-language">JavaScript</span></div>
        </div>
        <div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
        <div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">gl.clearColor(Math.random(),Math.random(),Math.random(), 1)</textarea></div>
        <div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
            <table class="crayon-table">
                <tbody>
                    <tr class="crayon-row">
                        <td class="crayon-nums " data-settings="show">
                            <div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;">
                                <div class="crayon-num" data-line="crayon-57b2a4e5a4492639824482-1" style="height: 15px;">1</div>
                            </div>
                        </td>
                        <td class="crayon-code">
                            <div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;">
                                <div class="crayon-line" id="crayon-57b2a4e5a4492639824482-1"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">clearColor</span><span class="crayon-sy">(</span><span class="crayon-v">Math</span><span class="crayon-sy">.</span><span class="crayon-e">random</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-v">Math</span><span class="crayon-sy">.</span><span class="crayon-e">random</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-v">Math</span><span class="crayon-sy">.</span><span class="crayon-e">random</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">1</span><span class="crayon-sy">)</span></div>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
    <!-- [Format Time: 0.0013 seconds] -->
    <small>gl Context에서 제공하는 clearColor를 사용하고 있습니다. clearColor는 종이의 색을 RGBA형식으로 지정하는 기능을 합니다.<br>
<strong>gl.clearColor(R,G,B,A)</strong><p></p>
<li>R,G,B의 경우 입력수치를 비율적으로 사용하셔도 됩니다.</li>
<li>0~255 범주의 형태로 사용하셔도 무방하다는! 단지 RGB의 비율에 따라서 색상이 결정됩니다. </li>
<li>A(alpha)의 경우는 무조건 0~1 사이의 값으로 사용합니다.</li>
</small>
    <p><small></small></p>
    <!-- Crayon Syntax Highlighter v2.6.9 -->

    <div id="crayon-57b2a4e5a449a972350290" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">

        <div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">gl.clear</span>
            <div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;">
                <div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-plain-button" title="일반 코드 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-copy-button" title="복사">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-popup-button" title="새 창에서 보기">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div><span class="crayon-language">JavaScript</span></div>
        </div>
        <div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
        <div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">gl.clear(gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT) // gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT에 대해서는 나중에…</textarea></div>
        <div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
            <table class="crayon-table">
                <tbody>
                    <tr class="crayon-row">
                        <td class="crayon-nums " data-settings="show">
                            <div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;">
                                <div class="crayon-num" data-line="crayon-57b2a4e5a449a972350290-1" style="height: 30px;">1</div>
                            </div>
                        </td>
                        <td class="crayon-code">
                            <div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;">
                                <div class="crayon-line" id="crayon-57b2a4e5a449a972350290-1"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">clear</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">COLOR_BUFFER_BIT</span><span class="crayon-h"> </span><span class="crayon-o">|</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">DEPTH_BUFFER_BIT</span><span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-c">// gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT에 대해서는 나중에…</span></div>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
    <!-- [Format Time: 0.0011 seconds] -->
    <p><small>gl.clear는 화면을 완전히 지워주는 기능을 합니다. </small></p>
    <hr>
    <center><strong>즉 위의 코드는 배경화면 색상을 지정하고 화면을 지우는 행위를 반복하고 있는 것!</strong></center>
    <p></p>
    <hr>
    <strong>그렇다면 어제 알아본 삼각형을 그리려면 그럼 어떻게?</strong>
    <!-- Crayon Syntax Highlighter v2.6.9 -->

    <div id="crayon-57b2a4e5a44a2704292831" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">

        <div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title"></span>
            <div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;">
                <div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-plain-button" title="일반 코드 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-copy-button" title="복사">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div>
                <div class="crayon-button crayon-popup-button" title="새 창에서 보기">
                    <div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div>
                </div><span class="crayon-language">JavaScript</span></div>
        </div>
        <div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
        <div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">gl.clearColor(Math.random(),Math.random(),Math.random(), 1) 
// 1. 배경색을 결정하고
gl.clear(gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT) 
// 2. 화면을 지운다음
// 3. 삼각형정보를 GPU에 업로드하고
// 4. Vertex Shader를 이용해서 Gemetry를 결정하고! 이동!!
// 5. Fragment Shader를 이용해서 색상을 지정하면
// 6. 삼각형이 그려집니다. </textarea></div>
        <div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
            <table class="crayon-table">
                <tbody>
                    <tr class="crayon-row">
                        <td class="crayon-nums " data-settings="show">
                            <div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;">
                                <div class="crayon-num" data-line="crayon-57b2a4e5a44a2704292831-1" style="height: 15px;">1</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a44a2704292831-2" style="height: 15px;">2</div>
                                <div class="crayon-num" data-line="crayon-57b2a4e5a44a2704292831-3" style="height: 15px;">3</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a44a2704292831-4" style="height: 15px;">4</div>
                                <div class="crayon-num" data-line="crayon-57b2a4e5a44a2704292831-5" style="height: 15px;">5</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a44a2704292831-6" style="height: 15px;">6</div>
                                <div class="crayon-num" data-line="crayon-57b2a4e5a44a2704292831-7" style="height: 15px;">7</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a4e5a44a2704292831-8" style="height: 15px;">8</div>
                            </div>
                        </td>
                        <td class="crayon-code">
                            <div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;">
                                <div class="crayon-line" id="crayon-57b2a4e5a44a2704292831-1"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">clearColor</span><span class="crayon-sy">(</span><span class="crayon-v">Math</span><span class="crayon-sy">.</span><span class="crayon-e">random</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-v">Math</span><span class="crayon-sy">.</span><span class="crayon-e">random</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-v">Math</span><span class="crayon-sy">.</span><span class="crayon-e">random</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">1</span><span class="crayon-sy">)</span><span class="crayon-h"> </span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a44a2704292831-2"><span class="crayon-c">// 1. 배경색을 결정하고</span></div>
                                <div class="crayon-line" id="crayon-57b2a4e5a44a2704292831-3"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">clear</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">COLOR_BUFFER_BIT</span><span class="crayon-h"> </span><span class="crayon-o">|</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">DEPTH_BUFFER_BIT</span><span class="crayon-sy">)</span><span class="crayon-h"> </span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a44a2704292831-4"><span class="crayon-c">// 2. 화면을 지운다음</span></div>
                                <div class="crayon-line" id="crayon-57b2a4e5a44a2704292831-5"><span class="crayon-c">// 3. 삼각형정보를 GPU에 업로드하고</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a44a2704292831-6"><span class="crayon-c">// 4. Vertex Shader를 이용해서 Gemetry를 결정하고! 이동!!</span></div>
                                <div class="crayon-line" id="crayon-57b2a4e5a44a2704292831-7"><span class="crayon-c">// 5. Fragment Shader를 이용해서 색상을 지정하면</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a4e5a44a2704292831-8"><span class="crayon-c">// 6. 삼각형이 그려집니다. </span></div>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
    <!-- [Format Time: 0.0024 seconds] -->
    한번에 여러 개를 그린다면 1번의 Render실행시 3~6번을 반복하면 되겠죠?<br> 003 연재에서는 3~6번을 진행하면서<br>
    <strong>Buffer</strong>와 <strong>Shader</strong>의 기초 입문을 진행하도록 하겠습니다~
    <p></p>
    <p><img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/0013.png" alt="001" width="100%" class="wp-image-404"></p>
    <div class="addthis_toolbox addthis_default_style addthis_32x32_style" addthis:url="http://www.bswebgl.com/?p=351" addthis:title="WebGL Study 002 – webGL 초기화와 Renderer "><a class="addthis_button_facebook at300b" title="Facebook" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(59, 89, 152);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="Facebook" alt="Facebook" style="width: 32px; height: 32px;" class="at-icon at-icon-facebook"><g><path d="M22 5.16c-.406-.054-1.806-.16-3.43-.16-3.4 0-5.733 1.825-5.733 5.17v2.882H9v3.913h3.837V27h4.604V16.965h3.823l.587-3.913h-4.41v-2.5c0-1.123.347-1.903 2.198-1.903H22V5.16z" fill-rule="evenodd"></path></g></svg></span></a><a class="addthis_button_twitter at300b" title="Tweet" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(29, 161, 242);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="Twitter" alt="Twitter" style="width: 32px; height: 32px;" class="at-icon at-icon-twitter"><g><path d="M27.996 10.116c-.81.36-1.68.602-2.592.71a4.526 4.526 0 0 0 1.984-2.496 9.037 9.037 0 0 1-2.866 1.095 4.513 4.513 0 0 0-7.69 4.116 12.81 12.81 0 0 1-9.3-4.715 4.49 4.49 0 0 0-.612 2.27 4.51 4.51 0 0 0 2.008 3.755 4.495 4.495 0 0 1-2.044-.564v.057a4.515 4.515 0 0 0 3.62 4.425 4.52 4.52 0 0 1-2.04.077 4.517 4.517 0 0 0 4.217 3.134 9.055 9.055 0 0 1-5.604 1.93A9.18 9.18 0 0 1 6 23.85a12.773 12.773 0 0 0 6.918 2.027c8.3 0 12.84-6.876 12.84-12.84 0-.195-.005-.39-.014-.583a9.172 9.172 0 0 0 2.252-2.336" fill-rule="evenodd"></path></g></svg></span></a><a class="addthis_button_email at300b" target="_blank" title="이메일" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(132, 132, 132);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="Email" alt="Email" style="width: 32px; height: 32px;" class="at-icon at-icon-email"><g><g fill-rule="evenodd"></g><path d="M27 22.757c0 1.24-.988 2.243-2.19 2.243H7.19C5.98 25 5 23.994 5 22.757V13.67c0-.556.39-.773.855-.496l8.78 5.238c.782.467 1.95.467 2.73 0l8.78-5.238c.472-.28.855-.063.855.495v9.087z"></path><path d="M27 9.243C27 8.006 26.02 7 24.81 7H7.19C5.988 7 5 8.004 5 9.243v.465c0 .554.385 1.232.857 1.514l9.61 5.733c.267.16.8.16 1.067 0l9.61-5.733c.473-.283.856-.96.856-1.514v-.465z"></path></g></svg></span></a><a class="addthis_button_pinterest_share at300b" target="_blank" title="Pinterest" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(203, 32, 39);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="Pinterest" alt="Pinterest" style="width: 32px; height: 32px;" class="at-icon at-icon-pinterest_share"><g><path d="M7 13.252c0 1.81.772 4.45 2.895 5.045.074.014.178.04.252.04.49 0 .772-1.27.772-1.63 0-.428-1.174-1.34-1.174-3.123 0-3.705 3.028-6.33 6.947-6.33 3.37 0 5.863 1.782 5.863 5.058 0 2.446-1.054 7.035-4.468 7.035-1.232 0-2.286-.83-2.286-2.018 0-1.742 1.307-3.43 1.307-5.225 0-1.092-.67-1.977-1.916-1.977-1.692 0-2.732 1.77-2.732 3.165 0 .774.104 1.63.476 2.336-.683 2.736-2.08 6.814-2.08 9.633 0 .87.135 1.728.224 2.6l.134.137.207-.07c2.494-3.178 2.405-3.8 3.533-7.96.61 1.077 2.182 1.658 3.43 1.658 5.254 0 7.614-4.77 7.614-9.067C26 7.987 21.755 5 17.094 5 12.017 5 7 8.15 7 13.252z" fill-rule="evenodd"></path></g></svg></span></a><a class="addthis_button_compact at300m" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(255, 101, 80);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="More" alt="More" style="width: 32px; height: 32px;" class="at-icon at-icon-addthis"><g><path d="M18 14V8h-4v6H8v4h6v6h4v-6h6v-4h-6z" fill-rule="evenodd"></path></g></svg></span></a><a class="addthis_counter addthis_bubble_style" href="#" style="display: inline-block;"><a class="addthis_button_expanded" target="_blank" title="더 보기" href="#">6</a><a class="atc_s addthis_button_compact"><span></span></a></a>
        <div class="atclear"></div>
    </div>
</div>
