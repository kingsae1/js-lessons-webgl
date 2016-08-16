<div class="entry-content">
    <p><strong>webGL Study 003</strong><br> 세번째 연재에서 다루게될 내용들은 아래와 같습니다.<br>
        <small>앞선 연재에 비해 내용도 많고 살짝 머리가 아픕니다. 실제로 약 2~3회분 정도의 내용이기도 하구요. 하지만 드디어 삼각형을 그려볼 수 있으니 -0-;;;;</small></p>
    <ol>
        <li>CPU와 GPU는 서로 관심이 없다….</li>
        <li>정점 Buffer</li>
        <li>Shader의 기초개념</li>
        <li>Program의 개념</li>
        <li>getAttribLocation와 Attribute</li>
        <li>Render 함수 업데이트하기</li>
    </ol>
    <hr>
    <strong>1.CPU와 GPU는 서로 몰라요..</strong><br>
    <small><br>
CPU와 GPU는 서로 입장에서 보면 마치 외국인과 같습니다. 한국말로 아무리 이야기해봐야 미국인이 한국어를 알아듣지 못하는 것과 같이 CPU와 GPU도 서로가 알아 들을 수 있는 형태로 의사 소통을 해야 합니다. <p></p>
<p></p><center><strong>그래서 마치 통역사와 같은 사람이 필요한데 webGL의 API가 이 역할을 대신합니다. </strong></center><br>
<img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/0014-1024x387.png" alt="001" width="584" height="220" class="alignleft size-large wp-image-424"><br>
라는 것이죠. 1,2연재를 통해서 gl컨텍스트를 얻었으니 GPU에게 우리는 이야기 할 수 있는 환경은 갖춰놓은 것이죠!<br>
</small>
    <p></p>
    <hr>
    <strong>2.정점 Buffer</strong><br>
    <small><br>
우선 삼각형이될 정점 정보를 배열로 선언해 보겠습니다.<br>
<!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251f9ac777237565" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">triangleData</span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">var triangleData = [
       0.0, 1.0, 0.0,
       -1.0, -1.0, 0.0,
       1.0, -1.0, 0.0
]</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251f9ac777237565-1" style="height: 15px;">1</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251f9ac777237565-2" style="height: 15px;">2</div><div class="crayon-num" data-line="crayon-57b2a5251f9ac777237565-3" style="height: 15px;">3</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251f9ac777237565-4" style="height: 15px;">4</div><div class="crayon-num" data-line="crayon-57b2a5251f9ac777237565-5" style="height: 15px;">5</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251f9ac777237565-1"><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">triangleData</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-sy">[</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251f9ac777237565-2"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">0.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">1.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0.0</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-57b2a5251f9ac777237565-3"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-o">-</span><span class="crayon-cn">1.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-o">-</span><span class="crayon-cn">1.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0.0</span><span class="crayon-sy">,</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251f9ac777237565-4"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">1.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-o">-</span><span class="crayon-cn">1.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0.0</span></div><div class="crayon-line" id="crayon-57b2a5251f9ac777237565-5"><span class="crayon-sy">]</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0017 seconds] -->
<img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/0041-300x249.png" alt="004" width="200" class="alignleft size-medium wp-image-429">JS 입장에서 보면 <strong>단순한 배열을 GPU에 업로드하면 그 배열을 Buffer</strong>라 부릅니다. 용어만 다를 뿐이죠.<p></p>
<hr>
GPU에 배열정보를 업로드 하기 위해서는 GPU상에서 버퍼를 우선 생성 해야 합니다.<br>
Javascript도 <strong>Var 변수이름 = [ ]</strong> 배열생성을 하듯이 GPU상에서 배열을 저장할 공간을 확보 해야 합니다.<br>
<!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251f9bf385444028" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">gl.createBuffer</span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">var triangleBuffer = gl.createBuffer()</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251f9bf385444028-1" style="height: 15px;">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251f9bf385444028-1"><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">triangleBuffer</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">createBuffer</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0007 seconds] -->
GPU상에서 Buffer를 생성하고 그 주소값을 triangleBuffer라는 자바스크립트 변수명에 저장합니다. webGL은 <strong>상태머신</strong>으로 작동합니다. 버퍼를 생성하는것은 단순히 GPU VRAM에 메모리공간을 잡았다라는 의미일 뿐이라서 <strong>이제부터 이 버퍼를 사용 할꺼야! 라고 꼭 알려 줘야 합니다..</strong><!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251f9c7828136120" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">gl.bindBuffer</span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">gl.bindBuffer(gl.ARRAY_BUFFER, triangleBuffer)
// bindBuffer를 통해서 생성한 버퍼를 GPU상에서 사용하겠다 라고 말합니다!</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251f9c7828136120-1" style="height: 15px;">1</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251f9c7828136120-2" style="height: 15px;">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251f9c7828136120-1"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">bindBuffer</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">ARRAY_BUFFER</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">)</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251f9c7828136120-2"><span class="crayon-c">// bindBuffer를 통해서 생성한 버퍼를 GPU상에서 사용하겠다 라고 말합니다!</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0010 seconds] -->
<br>
Buffer는 생성하고 GPU에 바인딩했으니 실질적인 데이터를 넣어줘야 합니다. webGL은 이 데이터 입력을 위해서 <strong>bufferData</strong>라는 API를 제공합니다.<br>
<!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251f9cf772965051" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">gl.bufferData</span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(triangleData), gl.STATIC_DRAW)</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251f9cf772965051-1" style="height: 30px;">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251f9cf772965051-1"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">bufferData</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">ARRAY_BUFFER</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-r">new</span><span class="crayon-h"> </span><span class="crayon-e">Float32Array</span><span class="crayon-sy">(</span><span class="crayon-v">triangleData</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">STATIC_DRAW</span><span class="crayon-sy">)</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0012 seconds] -->
를 통해서 CPU에 있는 데이터를 GPU로 옮겨 사용할 수 있는 형태로 만들 수 있게 됩니다. <p></p>
<hr>
<strong>gl.bufferData 인자</strong><p></p>
<ol>
<li><strong>첫번째 인자</strong>로 나오고 있는 gl.ARRAY_BUFFER는 버퍼의 타입을 뜻합니다. 세번째 나오는 gl.STATIC_DRAW와 함께 이후에 다시 다루겠습니다.</li>
<li><strong>두번째 인자</strong>로 Float32Array를 새로 만들어서 triangleData 배열을 입력하고 있습니다. webGL은 Float32Array와 같이 타입드 어레이를 사용합니다. 보다 빠른 연산을 위해 사용하고 있으니 주의 해야합니다.
</li>
</ol>
<hr>
생성된 버퍼는 triangleBuffer라는 자바 스크립트 변수에 담겨있습니다. 그래서 우리는 triangleBuffer에 임의로 어떠한 정보든 저장할 수 있습니다. <strong>배열로된 데이터를 x,y,z로 볼 때 정점이 3개다라는 의미로 나중에 해석할 근거</strong>를 주기 위해서<br>
<!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251f9d8682804857" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title"></span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">triangleBuffer.itemSize = 3; // 정점은 3개로 이루어져있고
triangleBuffer.numItem = 3 // 정점 3개로 트라이앵글을 구성한다!</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251f9d8682804857-1" style="height: 15px;">1</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251f9d8682804857-2" style="height: 15px;">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251f9d8682804857-1"><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">.</span><span class="crayon-v">itemSize</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-cn">3</span><span class="crayon-sy">;</span><span class="crayon-h"> </span><span class="crayon-c">// 정점은 3개로 이루어져있고</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251f9d8682804857-2"><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">.</span><span class="crayon-v">numItem</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-cn">3</span><span class="crayon-h"> </span><span class="crayon-c">// 정점 3개로 트라이앵글을 구성한다!</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0012 seconds] -->
와 같이 정보를 기록해 둡니다.<br>
console을 찍어보시면 생성된 버퍼와 itemSize, numItem을 가진 자바스크립트 오브젝트를 확인 하실 수 있습니다.<br>
<!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251f9e0799925766" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">Triangle Buffer 생성 코드 전문</span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">var triangleData = [
       0.0, 1.0, 0.0,
       -1.0, -1.0, 0.0,
       1.0, -1.0, 0.0
   ]
var triangleBuffer = gl.createBuffer()
// 1.버퍼생성
gl.bindBuffer(gl.ARRAY_BUFFER,triangleBuffer)
// 2.버퍼를 GPU에 바인딩
gl.bufferData(gl.ARRAY_BUFFER,new Float32Array(triangleData),gl.STATIC_DRAW)
// 3.버퍼에 데이터를 입력
triangleBuffer.itemSize = 3
triangleBuffer.numItem = 3
// 4.생성된 버퍼를 담아둔 JS 오브젝트에 추가정보입력
console.log(triangleBuffer)</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251f9e0799925766-1" style="height: 15px;">1</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251f9e0799925766-2" style="height: 15px;">2</div><div class="crayon-num" data-line="crayon-57b2a5251f9e0799925766-3" style="height: 15px;">3</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251f9e0799925766-4" style="height: 15px;">4</div><div class="crayon-num" data-line="crayon-57b2a5251f9e0799925766-5" style="height: 15px;">5</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251f9e0799925766-6" style="height: 15px;">6</div><div class="crayon-num" data-line="crayon-57b2a5251f9e0799925766-7" style="height: 15px;">7</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251f9e0799925766-8" style="height: 15px;">8</div><div class="crayon-num" data-line="crayon-57b2a5251f9e0799925766-9" style="height: 15px;">9</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251f9e0799925766-10" style="height: 30px;">10</div><div class="crayon-num" data-line="crayon-57b2a5251f9e0799925766-11" style="height: 15px;">11</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251f9e0799925766-12" style="height: 15px;">12</div><div class="crayon-num" data-line="crayon-57b2a5251f9e0799925766-13" style="height: 15px;">13</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251f9e0799925766-14" style="height: 15px;">14</div><div class="crayon-num" data-line="crayon-57b2a5251f9e0799925766-15" style="height: 15px;">15</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251f9e0799925766-1"><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">triangleData</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-sy">[</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251f9e0799925766-2"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">0.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">1.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0.0</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-57b2a5251f9e0799925766-3"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-o">-</span><span class="crayon-cn">1.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-o">-</span><span class="crayon-cn">1.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0.0</span><span class="crayon-sy">,</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251f9e0799925766-4"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">1.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-o">-</span><span class="crayon-cn">1.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0.0</span></div><div class="crayon-line" id="crayon-57b2a5251f9e0799925766-5"><span class="crayon-h">&nbsp;&nbsp; </span><span class="crayon-sy">]</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251f9e0799925766-6"><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">triangleBuffer</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">createBuffer</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span></div><div class="crayon-line" id="crayon-57b2a5251f9e0799925766-7"><span class="crayon-c">// 1.버퍼생성</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251f9e0799925766-8"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">bindBuffer</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">ARRAY_BUFFER</span><span class="crayon-sy">,</span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">)</span></div><div class="crayon-line" id="crayon-57b2a5251f9e0799925766-9"><span class="crayon-c">// 2.버퍼를 GPU에 바인딩</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251f9e0799925766-10"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">bufferData</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">ARRAY_BUFFER</span><span class="crayon-sy">,</span><span class="crayon-r">new</span><span class="crayon-h"> </span><span class="crayon-e">Float32Array</span><span class="crayon-sy">(</span><span class="crayon-v">triangleData</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">STATIC_DRAW</span><span class="crayon-sy">)</span></div><div class="crayon-line" id="crayon-57b2a5251f9e0799925766-11"><span class="crayon-c">// 3.버퍼에 데이터를 입력</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251f9e0799925766-12"><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">.</span><span class="crayon-v">itemSize</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-cn">3</span></div><div class="crayon-line" id="crayon-57b2a5251f9e0799925766-13"><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">.</span><span class="crayon-v">numItem</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-cn">3</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251f9e0799925766-14"><span class="crayon-c">// 4.생성된 버퍼를 담아둔 JS 오브젝트에 추가정보입력</span></div><div class="crayon-line" id="crayon-57b2a5251f9e0799925766-15"><span class="crayon-v">console</span><span class="crayon-sy">.</span><span class="crayon-e">log</span><span class="crayon-sy">(</span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">)</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0042 seconds] -->
<br>
<a href="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/0022.png"><img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/0022.png" alt="002" width="1212" height="912" class="alignleft size-full wp-image-425"></a><br>
하 고작 배열하나 생성하고 입력하는데 -_- 먼가 머리가 아파옵니다…(처음이라 그러니 -_- 적응하시길;;)<br>
</small>
    <p></p>
    <hr>
    <strong>3.Shader의 기초개념</strong><br>
    <small><br>
Shader는 GPU에서 돌아가는 작은 프로그램입니다. 사실 아주 간단하지만 설명하고 이해하기엔 오묘한 그런 녀석입니다.<p></p>
<hr><strong>Rasterize</strong><br>
쉐이더가 연산하는 대상은 Geometry상의 단위 영역입니다. 이 단위영역을 결정하는것은 바로 Rasterize라는 과정을 통해서 이루어집니다. 정점연결을 통해서 결정한 geometry는 수치 계산으로 이루어지게 됨으로 벡터라고 말할 수 있습니다. 이를 모니터상의 픽셀로 계산하는 과정을 레스터라이즈라고 말합니다. 레스터 라이즈화되면 지오메트리를 픽셀단위로 인식할 수 있게됩니다. 레스터라이즈과정은 <strong>Vertex Shader</strong>를 통해서 진행됩니다. <img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/0031.png" alt="003" width="735" height="272" class="alignleft size-full wp-image-428">레이터 라이즈화된 하나의 점 정보의 색상을 결정하는 일은 <strong>Fragment Shader</strong>의 일입니다. 따라서 반드시 2개의 쉐이더가 쌍으로 동작합니다. <p></p>
<p><strong></strong></p><center><strong>Shader의 연산대상은 당연히 레스터라이즈화된 모든 픽셀정보 입니다~!</strong></center><p></p>
<hr>
Shader라는 녀석도 Buffer와 마찬가지로 GPU상에서 구동됩니다. <strong>따라서 Buffer와 마찬가지로 webGL API를 이용해서 생성하고 데이터를 밀어 넣는 과정이 필요로 합니다.</strong> GPU는 시키지 않으면 아무것도 안하니까요;;<p></p>
<p><strong>Shader는 gl.createShader(타입)를 통해서 생성할 수 있습니다. </strong>이때 타입은 </p>
<ol>
<li>gl.VERTEX_SHADER</li>
<li>gl.FRAGMENT_SHADER</li>
</ol>
<p>중 하나를 사용합니다. Vertex Shader와 Fragment Shader를 타입 인자값을 통해서 생성할 수 있게 됩니다. 생성 후 쉐이더내에서 처리할 연산 프로그램 소스를 알려줘야 합니다. 버퍼와 마찬가지로 gl.createShader로 생성된 쉐이더는 빈 공간일 뿐이니까요.</p><!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251f9ea513567594" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">gl.shaderSource</span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">gl.shaderSource(대상쉐이더, 쉐이더소스) </textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251f9ea513567594-1" style="height: 15px;">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251f9ea513567594-1"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">shaderSource</span><span class="crayon-sy">(</span>대상쉐이더<span class="crayon-sy">,</span><span class="crayon-h"> </span>쉐이더소스<span class="crayon-sy">)</span><span class="crayon-h"> </span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0006 seconds] -->
<p>를 통해서 쉐이더 소스를 입력할 수 있습니다. </p>
<p>그런데 Shader는 GPU상에서 컴파일이라는 과정을 거쳐야합니다. 왜냐하면 쉐이더 소스는 C++로 작성되기 때문에 컴파일을 통해서 사용할 수 있는 프로그램으로 변경해야 합니다. 쉐이더 소스라는 것은 결국 자바스크립트로 작성된 소스가 넘어가게 될것인데 gl.shaderSource(대상쉐이더, 쉐이더소스)를 통해서 소스를 받은 GPU입장에서는 쉐이더 소스라는 것은 그저 문자열이기 때문입니다. 따라서 반드시 컴파일을 해야합니다.</p><!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251f9f2013991776" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">gl.compileShader</span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">gl.compileShader(대상쉐이더)</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251f9f2013991776-1" style="height: 15px;">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251f9f2013991776-1"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">compileShader</span><span class="crayon-sy">(</span>대상쉐이더<span class="crayon-sy">)</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0005 seconds] -->
<p><strong>Shader 생성과정을 전체 소스로 보면  </strong></p><!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251f9fa799949631" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">shader 생성</span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">var firstShader = gl.createShader(gl.VERTEX_SHADER)
gl.shaderSource(firstShader, 쉐이더소스) 
gl.compileShader(firstShader)</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251f9fa799949631-1" style="height: 15px;">1</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251f9fa799949631-2" style="height: 15px;">2</div><div class="crayon-num" data-line="crayon-57b2a5251f9fa799949631-3" style="height: 15px;">3</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251f9fa799949631-1"><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">firstShader</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">createShader</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">VERTEX_SHADER</span><span class="crayon-sy">)</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251f9fa799949631-2"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">shaderSource</span><span class="crayon-sy">(</span><span class="crayon-v">firstShader</span><span class="crayon-sy">,</span><span class="crayon-h"> </span>쉐이더소스<span class="crayon-sy">)</span><span class="crayon-h"> </span></div><div class="crayon-line" id="crayon-57b2a5251f9fa799949631-3"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">compileShader</span><span class="crayon-sy">(</span><span class="crayon-v">firstShader</span><span class="crayon-sy">)</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0014 seconds] -->
<p> </p>
<p>의 과정을 거치게 됩니다 </p>
<hr>
실제로 가장 작은단위의 Vertex Shader와 Fragment Shader 소스를 작성해 보겠습니다.<br>
<strong>Vertex Shader 소스</strong><br>
 <!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251fa02455376327" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">Vertex Shader Source</span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">var vertexShaderStr = ""+
    "attribute vec3 aVertexPosition;" +
    "void main(void) {" +
    " gl_Position = vec4(aVertexPosition, 1.0);" +
    "}"</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251fa02455376327-1" style="height: 15px;">1</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa02455376327-2" style="height: 15px;">2</div><div class="crayon-num" data-line="crayon-57b2a5251fa02455376327-3" style="height: 15px;">3</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa02455376327-4" style="height: 15px;">4</div><div class="crayon-num" data-line="crayon-57b2a5251fa02455376327-5" style="height: 15px;">5</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251fa02455376327-1"><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-e ">vertexShaderStr</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-s">""</span><span class="crayon-o">+</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa02455376327-2"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"attribute vec3 aVertexPosition;"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div><div class="crayon-line" id="crayon-57b2a5251fa02455376327-3"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"void main(void) {"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa02455376327-4"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">" gl_Position = vec4(aVertexPosition, 1.0);"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div><div class="crayon-line" id="crayon-57b2a5251fa02455376327-5"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"}"</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0011 seconds] -->
 Vertex Shader는 Geometry를 결정하는 역할을 한다고 했습니다. 즉 현재 연산되는 점을 어떤 위치에 찍을지를 최종 목적으로 합니다. 따라서 Vertex Shader는 대부분 <strong>gl_Position이라는 것을 결정하는 것으로 작성이 끝나게 됩니다. </strong><p></p>
<p></p><!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251fa0a948904204" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title"></span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">void main(void) {
    // 앞에서 무슨일이 벌어지던지!!!
    // 에러만 안난다면!!!
    // 결국엔 바로아래의 gl_Position에 어떠한 4벡터를 입력만 제대로 하면 되는것이죠.
    gl_Position = vec4(aVertexPosition, 1.0);
}</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251fa0a948904204-1" style="height: 15px;">1</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa0a948904204-2" style="height: 15px;">2</div><div class="crayon-num" data-line="crayon-57b2a5251fa0a948904204-3" style="height: 15px;">3</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa0a948904204-4" style="height: 30px;">4</div><div class="crayon-num" data-line="crayon-57b2a5251fa0a948904204-5" style="height: 15px;">5</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa0a948904204-6" style="height: 15px;">6</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251fa0a948904204-1"><span class="crayon-t">void</span><span class="crayon-h"> </span><span class="crayon-e">main</span><span class="crayon-sy">(</span><span class="crayon-t">void</span><span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-sy">{</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa0a948904204-2"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-c">// 앞에서 무슨일이 벌어지던지!!!</span></div><div class="crayon-line" id="crayon-57b2a5251fa0a948904204-3"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-c">// 에러만 안난다면!!!</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa0a948904204-4"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-c">// 결국엔 바로아래의 gl_Position에 어떠한 4벡터를 입력만 제대로 하면 되는것이죠.</span></div><div class="crayon-line" id="crayon-57b2a5251fa0a948904204-5"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl_Position</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-e">vec4</span><span class="crayon-sy">(</span><span class="crayon-v">aVertexPosition</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">1.0</span><span class="crayon-sy">)</span><span class="crayon-sy">;</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa0a948904204-6"><span class="crayon-sy">}</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0014 seconds] -->
<p> </p>
<p>Fragment Shader는 현재 연산되는 점의 최종 값을 결정하는 Shader입니다.<br>
<strong>쉐이더 소스</strong></p><!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251fa11346848849" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">Fragment Shader Source</span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">    var fragmentShaderStr = ""+
    "void main(void) {" +
    " gl_FragColor = vec4(1.0, 1.0, 1.0, 1.0);" +
    "}"</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251fa11346848849-1" style="height: 15px;">1</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa11346848849-2" style="height: 15px;">2</div><div class="crayon-num" data-line="crayon-57b2a5251fa11346848849-3" style="height: 15px;">3</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa11346848849-4" style="height: 15px;">4</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251fa11346848849-1"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-e ">fragmentShaderStr</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-s">""</span><span class="crayon-o">+</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa11346848849-2"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"void main(void) {"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div><div class="crayon-line" id="crayon-57b2a5251fa11346848849-3"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">" gl_FragColor = vec4(1.0, 1.0, 1.0, 1.0);"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa11346848849-4"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"}"</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0010 seconds] -->
<p> </p>
<p>최종적으로는 <strong>gl_FragColor에 4벡터(R,G,B,A) 값만 입력하는 것을 목적으로 합니다.</strong></p>
<p>앞서 배운 Shader 컴파일을 적용해보면</p><!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251fa19847688000" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">Shader 작성 코드전문</span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;"> // Vertex Shader
    var vertexShaderStr = ""+
    "attribute vec3 aVertexPosition;" +
    "void main(void) {" +
    " gl_Position = vec4(aVertexPosition, 1.0);" +
    "}"
    var vertexShader = gl.createShader(gl.VERTEX_SHADER)
    gl.shaderSource(vertexShader, vertexShaderStr)
    gl.compileShader(vertexShader)
    console.log(vertexShader)

    // Fragment Shader
    var fragmentShaderStr = ""+
    "void main(void) {" +
    " gl_FragColor = vec4(1.0, 1.0, 1.0, 1.0);" +
    "}"
    var fragmentShader = gl.createShader(gl.FRAGMENT_SHADER)
    gl.shaderSource(fragmentShader, fragmentShaderStr)
    gl.compileShader(fragmentShader)
    console.log(fragmentShader)</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251fa19847688000-1" style="height: 15px;">1</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa19847688000-2" style="height: 15px;">2</div><div class="crayon-num" data-line="crayon-57b2a5251fa19847688000-3" style="height: 15px;">3</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa19847688000-4" style="height: 15px;">4</div><div class="crayon-num" data-line="crayon-57b2a5251fa19847688000-5" style="height: 15px;">5</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa19847688000-6" style="height: 15px;">6</div><div class="crayon-num" data-line="crayon-57b2a5251fa19847688000-7" style="height: 15px;">7</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa19847688000-8" style="height: 15px;">8</div><div class="crayon-num" data-line="crayon-57b2a5251fa19847688000-9" style="height: 15px;">9</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa19847688000-10" style="height: 15px;">10</div><div class="crayon-num" data-line="crayon-57b2a5251fa19847688000-11" style="height: 15px;">11</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa19847688000-12" style="height: 15px;">12</div><div class="crayon-num" data-line="crayon-57b2a5251fa19847688000-13" style="height: 15px;">13</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa19847688000-14" style="height: 15px;">14</div><div class="crayon-num" data-line="crayon-57b2a5251fa19847688000-15" style="height: 15px;">15</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa19847688000-16" style="height: 15px;">16</div><div class="crayon-num" data-line="crayon-57b2a5251fa19847688000-17" style="height: 15px;">17</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa19847688000-18" style="height: 15px;">18</div><div class="crayon-num" data-line="crayon-57b2a5251fa19847688000-19" style="height: 15px;">19</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa19847688000-20" style="height: 15px;">20</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251fa19847688000-1"><span class="crayon-h"> </span><span class="crayon-c">// Vertex Shader</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa19847688000-2"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-e ">vertexShaderStr</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-s">""</span><span class="crayon-o">+</span></div><div class="crayon-line" id="crayon-57b2a5251fa19847688000-3"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"attribute vec3 aVertexPosition;"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa19847688000-4"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"void main(void) {"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div><div class="crayon-line" id="crayon-57b2a5251fa19847688000-5"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">" gl_Position = vec4(aVertexPosition, 1.0);"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa19847688000-6"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"}"</span></div><div class="crayon-line" id="crayon-57b2a5251fa19847688000-7"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">vertexShader</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">createShader</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">VERTEX_SHADER</span><span class="crayon-sy">)</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa19847688000-8"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">shaderSource</span><span class="crayon-sy">(</span><span class="crayon-v">vertexShader</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">vertexShaderStr</span><span class="crayon-sy">)</span></div><div class="crayon-line" id="crayon-57b2a5251fa19847688000-9"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">compileShader</span><span class="crayon-sy">(</span><span class="crayon-v">vertexShader</span><span class="crayon-sy">)</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa19847688000-10"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">console</span><span class="crayon-sy">.</span><span class="crayon-e">log</span><span class="crayon-sy">(</span><span class="crayon-v">vertexShader</span><span class="crayon-sy">)</span></div><div class="crayon-line" id="crayon-57b2a5251fa19847688000-11">&nbsp;</div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa19847688000-12"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-c">// Fragment Shader</span></div><div class="crayon-line" id="crayon-57b2a5251fa19847688000-13"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-e ">fragmentShaderStr</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-s">""</span><span class="crayon-o">+</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa19847688000-14"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"void main(void) {"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div><div class="crayon-line" id="crayon-57b2a5251fa19847688000-15"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">" gl_FragColor = vec4(1.0, 1.0, 1.0, 1.0);"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa19847688000-16"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"}"</span></div><div class="crayon-line" id="crayon-57b2a5251fa19847688000-17"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">fragmentShader</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">createShader</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">FRAGMENT_SHADER</span><span class="crayon-sy">)</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa19847688000-18"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">shaderSource</span><span class="crayon-sy">(</span><span class="crayon-v">fragmentShader</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">fragmentShaderStr</span><span class="crayon-sy">)</span></div><div class="crayon-line" id="crayon-57b2a5251fa19847688000-19"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">compileShader</span><span class="crayon-sy">(</span><span class="crayon-v">fragmentShader</span><span class="crayon-sy">)</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa19847688000-20"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">console</span><span class="crayon-sy">.</span><span class="crayon-e">log</span><span class="crayon-sy">(</span><span class="crayon-v">fragmentShader</span><span class="crayon-sy">)</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0053 seconds] -->
<p> 로 정리 할 수 있습니다. </p>
</small>
    <p><small></small></p>
    <hr>
    <strong>4.Program의 개념</strong><br>
    <small><br>
험난하게 Shader를 이해했지만 Shader는 단독으로 사용되지 않습니다. 반드시 Vertex Shader와 Fragment Shader가 합쳐진 Program이라는 개념으로 사용됩니다. 역시나 GPU는 알려주지 않으면 아무것도 모르기 때문에 webGL API를 통해서 Program을 생성하고 앞서 만든 쉐이더를 연결해 주어야 합니다. <!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251fa22444187980" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">gl.createProgram</span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">Var firstProgram = gl.createProgram()
gl.attatchShader(firstProgram, 버텍스 쉐이더)
gl.attatchShader(firstProgram, 프레그먼트 쉐이더)
gl.linkProgram(firstProgram)</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251fa22444187980-1" style="height: 15px;">1</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa22444187980-2" style="height: 15px;">2</div><div class="crayon-num" data-line="crayon-57b2a5251fa22444187980-3" style="height: 15px;">3</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa22444187980-4" style="height: 15px;">4</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251fa22444187980-1"><span class="crayon-t">Var</span><span class="crayon-h"> </span><span class="crayon-v">firstProgram</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">createProgram</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa22444187980-2"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">attatchShader</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">,</span><span class="crayon-h"> </span>버텍스<span class="crayon-h"> </span>쉐이더<span class="crayon-sy">)</span></div><div class="crayon-line" id="crayon-57b2a5251fa22444187980-3"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">attatchShader</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">,</span><span class="crayon-h"> </span>프레그먼트<span class="crayon-h"> </span>쉐이더<span class="crayon-sy">)</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa22444187980-4"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">linkProgram</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">)</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0018 seconds] -->
향후 프로그램을 사용할때는 <!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251fa29241094363" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title"></span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">gl.useProgram(대상 프로그램) </textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251fa29241094363-1" style="height: 15px;">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251fa29241094363-1"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">useProgram</span><span class="crayon-sy">(</span>대상<span class="crayon-h"> </span>프로그램<span class="crayon-sy">)</span><span class="crayon-h"> </span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0006 seconds] -->
 을 통해서 사용하게 됩니다. <strong>앞서 말씀드린 것 처럼 webGL은 상태 머신의 개념으로 작동하기 때문이죠.</strong><br>
</small>
    <p></p>
    <hr>
    <strong>5.갑자기 너무 어려운 것 같아요…!!!</strong><br>
    <small><br>
겨우 3강만에 갑자기 난이도가 극 상승 한 것처럼 보이지만! 용어와 개념이 아직 익숙하지 않을 것 뿐이니 너무 걱정하지 않으셔도 됩니다. 지금까지 제가 말씀 드리고 있는 건 단어 몇 개와 <strong>GPU상에 뭔가 생성하고 업데이트 하려면 일일이 다 알려줘야 된다라는 이야기를 반복</strong>하고 있을 뿐이랍니다.<br>
^^ 그렇지 않다면 제 설명이 -_-;;;;;;;;;;;;;;<br>
댓글로 이해가 잘 되지 않는 부분을 알려주시면 업데이트 하는 방향으로 ;;;<br>
</small>
    <p></p>
    <hr>
    <strong>6. getAttribLocation와 Attribute</strong><br>
    <small><br>
render함수를 변경하기 전 Shader에 있는 어떤 변수(?)에 어떻게 접근하는지부터 알아봅니다.<br>
앞선 Vertex Shader 소스를 작성할 때 <strong>Attribute vec3 aVertexPosition;</strong> 이라는 것을 작성했습니다. 이는 aVertexPosition으로 3개의 요소로 구성된 벡터를 한 개의 정점으로 보겠다고 선언한 것입니다.<br>
<strong>gl.getAttribLocation</strong>을 이용해서 선언한 aVertexPosition의 주소를 알아올 수 있습니다.<br>
<!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251fa32993578449" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title"></span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">firstProgram.aVertexPosition = gl.getAttribLocation(firstProgram, "aVertexPosition");</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251fa32993578449-1" style="height: 30px;">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251fa32993578449-1"><span class="crayon-v">firstProgram</span><span class="crayon-sy">.</span><span class="crayon-v">aVertexPosition</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">getAttribLocation</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-s">"aVertexPosition"</span><span class="crayon-sy">)</span><span class="crayon-sy">;</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0010 seconds] -->
 통해서 미리 주소를 알아내어 <strong>firstProgram.aVertexPosition</strong>에 저장해 둡니다.<br>
<a href="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/0051.png"><img src="http://www.bswebgl.com/wp/wp-content/uploads/2014/10/0051.png" alt="005" width="1207" height="558" class="alignleft size-full wp-image-430"></a><br>
</small>
    <p></p>
    <hr>
    <strong>7. Render 함수 업데이트하기</strong><br>
    <small><br>
Triangle 정점 Buffer도 생성했고 삼각형을 그려낼 Vertex Shader와 Fragment Shader를 준비가 되었습니다. 이를 이용하여 <strong>render 함수에서 삼각형을 그려내 보겠습니다.</strong> 우선 어떤 Shader를 사용하겠다라고 GPU에게 알려줍니다. 그리고 사용할 정점버퍼인 triangleBuffer도 알려줍니다.<br>
<!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251fa3a234256039" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title"></span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">gl.useProgram(fristProgram)
gl.bindBuffer(gl.ARRAY_BUFFER, triangleBuffer)</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251fa3a234256039-1" style="height: 15px;">1</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa3a234256039-2" style="height: 15px;">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251fa3a234256039-1"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">useProgram</span><span class="crayon-sy">(</span><span class="crayon-v">fristProgram</span><span class="crayon-sy">)</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa3a234256039-2"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">bindBuffer</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">ARRAY_BUFFER</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">)</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0010 seconds] -->
여기서 <strong>vertexAttribPointer </strong>개념이 다시 등장합니다. vertexAttribPointer는 1개의 정점을 어떻게 결정할 것인가를 판단할 인자들을 설정하는 것입니다. 따라서 앞서 삼강형 Buffer에 저장해둔 <strong>아이템 사이즈</strong>와 <strong>아이템 갯수</strong>를 GPU에게 알려줍니다.<!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251fa42696356979" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title"></span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">gl.enableVertexAttribArray(firstProgram.aVertexPosition);
gl.vertexAttribPoint(firstProgram.aVertexPosition, triangleBuffer.itemSize, gl.FLOAT, false, 0,0)</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251fa42696356979-1" style="height: 15px;">1</div><div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa42696356979-2" style="height: 30px;">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251fa42696356979-1"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">enableVertexAttribArray</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">.</span><span class="crayon-v">aVertexPosition</span><span class="crayon-sy">)</span><span class="crayon-sy">;</span></div><div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa42696356979-2"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">vertexAttribPoint</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">.</span><span class="crayon-v">aVertexPosition</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">.</span><span class="crayon-v">itemSize</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-t">FLOAT</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-t">false</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0</span><span class="crayon-sy">,</span><span class="crayon-cn">0</span><span class="crayon-sy">)</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0018 seconds] -->
3개의 단위로 하나의 정점을 결정(x,y,z)하고 Float 형으로 사용하겠다 입니다.<br>
<!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251fa49257872342" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title"></span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">gl.drawArrays(gl.TRIANGLES,0, triangleBuffer.numItem)</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251fa49257872342-1" style="height: 15px;">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251fa49257872342-1"><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">drawArrays</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">TRIANGLES</span><span class="crayon-sy">,</span><span class="crayon-cn">0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">.</span><span class="crayon-v">numItem</span><span class="crayon-sy">)</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0009 seconds] -->
드디어 삼각형을 호출합니다. webGl을 통해서 무언가를 화면에 그려내기 위해서는 모든 준비과정을 마친뒤 <strong>drawArrays 같은 호출 API</strong>를 사용합니다.<br>
<!-- Crayon Syntax Highlighter v2.6.9 -->

		<div id="crayon-57b2a5251fa51916727266" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">
		
			<div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title"></span>
			<div class="crayon-tools" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><div class="crayon-button crayon-nums-button crayon-pressed" title="줄 번호 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-plain-button" title="일반 코드 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-wrap-button crayon-pressed" title="줄 바꿈 토글"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기" style="display: none;"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-copy-button" title="복사"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><div class="crayon-button crayon-popup-button" title="새 창에서 보기"><div class="crayon-button-icon" style="background-image: url(&quot;http://www.bswebgl.com/wp/wp-content/plugins/crayon-syntax-highlighter/css/images/toolbar/buttons@2x.png&quot;); background-size: 48px 128px;"></div></div><span class="crayon-language">JavaScript</span></div></div>
			<div class="crayon-info" style="min-height: 16.8px !important; line-height: 16.8px !important;"></div>
			<div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">drawwArray(정점을 어떤방식으로 연결할것인가, 몇번째 데이터 부터 인식 할 것인가, 몇 개의 정점을 그릴것인가)</textarea></div>
			<div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
				<table class="crayon-table">
					<tbody><tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;"><div class="crayon-num" data-line="crayon-57b2a5251fa51916727266-1" style="height: 30px;">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;"><div class="crayon-line" id="crayon-57b2a5251fa51916727266-1"><span class="crayon-e">drawwArray</span><span class="crayon-sy">(</span>정점을<span class="crayon-h"> </span>어떤방식으로<span class="crayon-h"> </span>연결할것인가<span class="crayon-sy">,</span><span class="crayon-h"> </span>몇번째<span class="crayon-h"> </span>데이터<span class="crayon-h"> </span>부터<span class="crayon-h"> </span>인식<span class="crayon-h"> </span>할<span class="crayon-h"> </span>것인가<span class="crayon-sy">,</span><span class="crayon-h"> </span>몇<span class="crayon-h"> </span>개의<span class="crayon-h"> </span>정점을<span class="crayon-h"> </span>그릴것인가<span class="crayon-sy">)</span></div></div></td>
					</tr>
				</tbody></table>
			</div>
		</div>
<!-- [Format Time: 0.0013 seconds] -->
</small><iframe src="/blog/003/index2.html" width="100%" height="300" scrolling="no"></iframe>
    <p></p>
    <hr>
    <p></p>
    <!-- Crayon Syntax Highlighter v2.6.9 -->

    <div id="crayon-57b2a5251fa58821350150" class="crayon-syntax crayon-theme-coda-special-board crayon-font-monaco crayon-os-mac print-yes notranslate crayon-wrapped" data-settings=" minimize scroll-mouseover wrap" style="margin-top: 12px; margin-bottom: 12px; font-size: 12px !important; line-height: 15px !important; height: auto;">

        <div class="crayon-toolbar" data-settings=" show" style="font-size: 12px !important;height: 18px !important; line-height: 18px !important;"><span class="crayon-title">코드전문</span>
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
                <div class="crayon-button crayon-expand-button" title="코드를 펼쳐서 보기">
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
        <div class="crayon-plain-wrap"><textarea class="crayon-plain print-no" data-settings="dblclick" readonly="" style="tab-size: 4; font-size: 12px !important; line-height: 15px !important; z-index: 0; opacity: 0; overflow: hidden;">&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head lang="en"&gt;
    &lt;meta charset="UTF-8"&gt;
    &lt;title&gt;&lt;/title&gt;
    &lt;style&gt;body, html {
        width: 100%;
        padding: 0px;
        margin: 0px
    }&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;canvas id="glCanvas" &gt;&lt;/canvas&gt;
&lt;script&gt;
    var gl, keys = 'webgl,experimental-webgl,webkit-3d,moz-webgl'.split(','), i = keys.length
    var cvs = document.getElementById('glCanvas')
    while (i--) if (gl = cvs.getContext(keys[i])) break
    if (gl) console.log('webgl 초기화 성공!')
    else console.log('webgl 초기화 실패!')

    // Vertex Buffer
    var triangleData = [
        0.0, .5, 0.0,
        -.5, -.5, 0.0,
        .5, -.5, 0.0
    ]
    var triangleBuffer = gl.createBuffer()
    gl.bindBuffer(gl.ARRAY_BUFFER, triangleBuffer)
    gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(triangleData), gl.STATIC_DRAW)
    triangleBuffer.itemSize = 3
    triangleBuffer.numItem = 3
    console.log(triangleBuffer)

    // Vertex Shader
    var vertexShaderStr = ""+
    "attribute vec3 aVertexPosition;" +
    "void main(void) {" +
    " gl_Position = vec4(aVertexPosition, 1.0);" +
    "}"
    var vertexShader = gl.createShader(gl.VERTEX_SHADER)
    gl.shaderSource(vertexShader, vertexShaderStr)
    gl.compileShader(vertexShader)
    console.log(vertexShader)

    // Fragment Shader
    var fragmentShaderStr = ""+
    "void main(void) {" +
    " gl_FragColor = vec4(1.0, 1.0, 1.0, 1.0);" +
    "}"
    var fragmentShader = gl.createShader(gl.FRAGMENT_SHADER)
    gl.shaderSource(fragmentShader, fragmentShaderStr)
    gl.compileShader(fragmentShader)
    console.log(fragmentShader)

    var firstProgram = gl.createProgram()
    gl.attachShader(firstProgram, vertexShader)
    gl.attachShader(firstProgram, fragmentShader)
    gl.linkProgram(firstProgram)
    console.log(firstProgram)

    firstProgram.aVertexPosition = gl.getAttribLocation(firstProgram, "aVertexPosition");



    function render(){
        gl.clearColor(Math.random(), Math.random(), Math.random(), 1)
        gl.clear(gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT)
        gl.useProgram(firstProgram)
        gl.bindBuffer(gl.ARRAY_BUFFER, triangleBuffer);
        gl.enableVertexAttribArray(firstProgram.aVertexPosition);
        gl.vertexAttribPointer(firstProgram.aVertexPosition, triangleBuffer.itemSize, gl.FLOAT, false, 0, 0);
        gl.drawArrays(gl.TRIANGLES, 0, triangleBuffer.numItem);
    }
    if(cvs)  cvs.width='450', cvs.height='300'
    gl.viewport(0, 0, parseInt(cvs.width), +parseInt(cvs.height));
    setInterval(render, 16)
&lt;/script&gt;

&lt;/body&gt;
&lt;/html&gt;</textarea></div>
        <div class="crayon-main" style="position: relative; z-index: 1; overflow: hidden;">
            <table class="crayon-table">
                <tbody>
                    <tr class="crayon-row">
                        <td class="crayon-nums " data-settings="show">
                            <div class="crayon-nums-content" style="font-size: 12px !important; line-height: 15px !important;">
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-1" style="height: 15px;">1</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-2" style="height: 15px;">2</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-3" style="height: 15px;">3</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-4" style="height: 15px;">4</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-5" style="height: 15px;">5</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-6" style="height: 15px;">6</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-7" style="height: 15px;">7</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-8" style="height: 15px;">8</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-9" style="height: 15px;">9</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-10" style="height: 15px;">10</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-11" style="height: 15px;">11</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-12" style="height: 15px;">12</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-13" style="height: 15px;">13</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-14" style="height: 15px;">14</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-15" style="height: 30px;">15</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-16" style="height: 15px;">16</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-17" style="height: 15px;">17</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-18" style="height: 15px;">18</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-19" style="height: 15px;">19</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-20" style="height: 15px;">20</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-21" style="height: 15px;">21</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-22" style="height: 15px;">22</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-23" style="height: 15px;">23</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-24" style="height: 15px;">24</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-25" style="height: 15px;">25</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-26" style="height: 15px;">26</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-27" style="height: 15px;">27</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-28" style="height: 15px;">28</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-29" style="height: 30px;">29</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-30" style="height: 15px;">30</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-31" style="height: 15px;">31</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-32" style="height: 15px;">32</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-33" style="height: 15px;">33</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-34" style="height: 15px;">34</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-35" style="height: 15px;">35</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-36" style="height: 15px;">36</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-37" style="height: 15px;">37</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-38" style="height: 15px;">38</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-39" style="height: 15px;">39</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-40" style="height: 15px;">40</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-41" style="height: 15px;">41</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-42" style="height: 15px;">42</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-43" style="height: 15px;">43</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-44" style="height: 15px;">44</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-45" style="height: 15px;">45</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-46" style="height: 15px;">46</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-47" style="height: 15px;">47</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-48" style="height: 15px;">48</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-49" style="height: 15px;">49</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-50" style="height: 15px;">50</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-51" style="height: 15px;">51</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-52" style="height: 15px;">52</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-53" style="height: 15px;">53</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-54" style="height: 15px;">54</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-55" style="height: 15px;">55</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-56" style="height: 15px;">56</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-57" style="height: 15px;">57</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-58" style="height: 15px;">58</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-59" style="height: 15px;">59</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-60" style="height: 15px;">60</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-61" style="height: 30px;">61</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-62" style="height: 15px;">62</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-63" style="height: 15px;">63</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-64" style="height: 15px;">64</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-65" style="height: 15px;">65</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-66" style="height: 30px;">66</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-67" style="height: 15px;">67</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-68" style="height: 15px;">68</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-69" style="height: 15px;">69</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-70" style="height: 15px;">70</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-71" style="height: 30px;">71</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-72" style="height: 15px;">72</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-73" style="height: 15px;">73</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-74" style="height: 15px;">74</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-75" style="height: 30px;">75</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-76" style="height: 15px;">76</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-77" style="height: 15px;">77</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-78" style="height: 15px;">78</div>
                                <div class="crayon-num" data-line="crayon-57b2a5251fa58821350150-79" style="height: 15px;">79</div>
                                <div class="crayon-num crayon-striped-num" data-line="crayon-57b2a5251fa58821350150-80" style="height: 15px;">80</div>
                            </div>
                        </td>
                        <td class="crayon-code">
                            <div class="crayon-pre" style="font-size: 12px !important; line-height: 15px !important; -moz-tab-size:4; -o-tab-size:4; -webkit-tab-size:4; tab-size:4;">
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-1"><span class="crayon-o">&lt;</span><span class="crayon-o">!</span><span class="crayon-e">DOCTYPE </span><span class="crayon-v">html</span><span class="crayon-o">&gt;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-2"><span class="crayon-o">&lt;</span><span class="crayon-v">html</span><span class="crayon-o">&gt;</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-3"><span class="crayon-o">&lt;</span><span class="crayon-e">head </span><span class="crayon-e ">lang</span><span class="crayon-o">=</span><span class="crayon-s">"en"</span><span class="crayon-o">&gt;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-4"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-o">&lt;</span><span class="crayon-e">meta </span><span class="crayon-e ">charset</span><span class="crayon-o">=</span><span class="crayon-s">"UTF-8"</span><span class="crayon-o">&gt;</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-5"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-o">&lt;</span><span class="crayon-e">title</span><span class="crayon-o">&gt;</span><span class="crayon-o">&lt;</span><span class="crayon-o">/</span><span class="crayon-e">title</span><span class="crayon-o">&gt;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-6"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-ta">&lt;style&gt;</span><span class="crayon-k ">body, html </span><span class="crayon-sy">{</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-7"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-e ">width</span><span class="crayon-sy">:</span><span class="crayon-h"> </span><span class="crayon-i ">100%</span><span class="crayon-sy">;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-8"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-e ">padding</span><span class="crayon-sy">:</span><span class="crayon-h"> </span><span class="crayon-i ">0px</span><span class="crayon-sy">;</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-9"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-e ">margin</span><span class="crayon-sy">:</span><span class="crayon-h"> </span><span class="crayon-i ">0px</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-10"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-sy">}</span><span class="crayon-ta">&lt;/style&gt;</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-11"><span class="crayon-o">&lt;</span><span class="crayon-o">/</span><span class="crayon-v">head</span><span class="crayon-o">&gt;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-12"><span class="crayon-o">&lt;</span><span class="crayon-v">body</span><span class="crayon-o">&gt;</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-13"><span class="crayon-o">&lt;</span><span class="crayon-e">canvas </span><span class="crayon-e ">id</span><span class="crayon-o">=</span><span class="crayon-s">"glCanvas"</span><span class="crayon-h"> </span><span class="crayon-o">&gt;</span><span class="crayon-o">&lt;</span><span class="crayon-o">/</span><span class="crayon-e">canvas</span><span class="crayon-o">&gt;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-14"><span class="crayon-ta">&lt;script&gt;</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-15"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-e ">keys</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-s">'webgl,experimental-webgl,webkit-3d,moz-webgl'</span><span class="crayon-sy">.</span><span class="crayon-e">split</span><span class="crayon-sy">(</span><span class="crayon-s">','</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">i</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">keys</span><span class="crayon-sy">.</span><span class="crayon-e">length</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-16"><span class="crayon-e">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">cvs</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">document</span><span class="crayon-sy">.</span><span class="crayon-e">getElementById</span><span class="crayon-sy">(</span><span class="crayon-s">'glCanvas'</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-17"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-st">while</span><span class="crayon-h"> </span><span class="crayon-sy">(</span><span class="crayon-v">i</span><span class="crayon-o">--</span><span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-st">if</span><span class="crayon-h"> </span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">cvs</span><span class="crayon-sy">.</span><span class="crayon-e">getContext</span><span class="crayon-sy">(</span><span class="crayon-v">keys</span><span class="crayon-sy">[</span><span class="crayon-v">i</span><span class="crayon-sy">]</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-st">break</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-18"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-st">if</span><span class="crayon-h"> </span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-v">console</span><span class="crayon-sy">.</span><span class="crayon-e">log</span><span class="crayon-sy">(</span><span class="crayon-s">'webgl 초기화 성공!'</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-19"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-st">else</span><span class="crayon-h"> </span><span class="crayon-v">console</span><span class="crayon-sy">.</span><span class="crayon-e">log</span><span class="crayon-sy">(</span><span class="crayon-s">'webgl 초기화 실패!'</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-20">&nbsp;</div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-21"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-c">// Vertex Buffer</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-22"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">triangleData</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-sy">[</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-23"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-cn">0.0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-sy">.</span><span class="crayon-cn">5</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0.0</span><span class="crayon-sy">,</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-24"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-o">-</span><span class="crayon-sy">.</span><span class="crayon-cn">5</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-o">-</span><span class="crayon-sy">.</span><span class="crayon-cn">5</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0.0</span><span class="crayon-sy">,</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-25"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-sy">.</span><span class="crayon-cn">5</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-o">-</span><span class="crayon-sy">.</span><span class="crayon-cn">5</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0.0</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-26"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-sy">]</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-27"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">triangleBuffer</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">createBuffer</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-28"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">bindBuffer</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">ARRAY_BUFFER</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-29"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">bufferData</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">ARRAY_BUFFER</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-r">new</span><span class="crayon-h"> </span><span class="crayon-e">Float32Array</span><span class="crayon-sy">(</span><span class="crayon-v">triangleData</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">STATIC_DRAW</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-30"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">.</span><span class="crayon-v">itemSize</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-cn">3</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-31"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">.</span><span class="crayon-v">numItem</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-cn">3</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-32"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">console</span><span class="crayon-sy">.</span><span class="crayon-e">log</span><span class="crayon-sy">(</span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-33">&nbsp;</div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-34"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-c">// Vertex Shader</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-35"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-e ">vertexShaderStr</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-s">""</span><span class="crayon-o">+</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-36"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"attribute vec3 aVertexPosition;"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-37"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"void main(void) {"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-38"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">" gl_Position = vec4(aVertexPosition, 1.0);"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-39"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"}"</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-40"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">vertexShader</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">createShader</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">VERTEX_SHADER</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-41"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">shaderSource</span><span class="crayon-sy">(</span><span class="crayon-v">vertexShader</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">vertexShaderStr</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-42"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">compileShader</span><span class="crayon-sy">(</span><span class="crayon-v">vertexShader</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-43"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">console</span><span class="crayon-sy">.</span><span class="crayon-e">log</span><span class="crayon-sy">(</span><span class="crayon-v">vertexShader</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-44">&nbsp;</div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-45"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-c">// Fragment Shader</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-46"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-e ">fragmentShaderStr</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-s">""</span><span class="crayon-o">+</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-47"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"void main(void) {"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-48"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">" gl_FragColor = vec4(1.0, 1.0, 1.0, 1.0);"</span><span class="crayon-h"> </span><span class="crayon-o">+</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-49"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-s">"}"</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-50"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">fragmentShader</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">createShader</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">FRAGMENT_SHADER</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-51"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">shaderSource</span><span class="crayon-sy">(</span><span class="crayon-v">fragmentShader</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">fragmentShaderStr</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-52"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">compileShader</span><span class="crayon-sy">(</span><span class="crayon-v">fragmentShader</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-53"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">console</span><span class="crayon-sy">.</span><span class="crayon-e">log</span><span class="crayon-sy">(</span><span class="crayon-v">fragmentShader</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-54">&nbsp;</div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-55"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">var</span><span class="crayon-h"> </span><span class="crayon-v">firstProgram</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">createProgram</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-56"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">attachShader</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">vertexShader</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-57"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">attachShader</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">fragmentShader</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-58"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">linkProgram</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-59"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">console</span><span class="crayon-sy">.</span><span class="crayon-e">log</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-60">&nbsp;</div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-61"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">.</span><span class="crayon-v">aVertexPosition</span><span class="crayon-h"> </span><span class="crayon-o">=</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">getAttribLocation</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-s">"aVertexPosition"</span><span class="crayon-sy">)</span><span class="crayon-sy">;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-62">&nbsp;</div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-63">&nbsp;</div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-64">&nbsp;</div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-65"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-t">function</span><span class="crayon-h"> </span><span class="crayon-e">render</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">{</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-66"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">clearColor</span><span class="crayon-sy">(</span><span class="crayon-v">Math</span><span class="crayon-sy">.</span><span class="crayon-e">random</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">Math</span><span class="crayon-sy">.</span><span class="crayon-e">random</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">Math</span><span class="crayon-sy">.</span><span class="crayon-e">random</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">1</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-67"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">clear</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">COLOR_BUFFER_BIT</span><span class="crayon-h"> </span><span class="crayon-o">|</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">DEPTH_BUFFER_BIT</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-68"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">useProgram</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-69"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">bindBuffer</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">ARRAY_BUFFER</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">)</span><span class="crayon-sy">;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-70"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">enableVertexAttribArray</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">.</span><span class="crayon-v">aVertexPosition</span><span class="crayon-sy">)</span><span class="crayon-sy">;</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-71"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">vertexAttribPointer</span><span class="crayon-sy">(</span><span class="crayon-v">firstProgram</span><span class="crayon-sy">.</span><span class="crayon-v">aVertexPosition</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">.</span><span class="crayon-v">itemSize</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-t">FLOAT</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-t">false</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0</span><span class="crayon-sy">)</span><span class="crayon-sy">;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-72"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">drawArrays</span><span class="crayon-sy">(</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-v">TRIANGLES</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">triangleBuffer</span><span class="crayon-sy">.</span><span class="crayon-v">numItem</span><span class="crayon-sy">)</span><span class="crayon-sy">;</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-73"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-sy">}</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-74"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-st">if</span><span class="crayon-sy">(</span><span class="crayon-v">cvs</span><span class="crayon-sy">)</span><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-v">cvs</span><span class="crayon-sy">.</span><span class="crayon-e ">width</span><span class="crayon-o">=</span><span class="crayon-s">'450'</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">cvs</span><span class="crayon-sy">.</span><span class="crayon-e ">height</span><span class="crayon-o">=</span><span class="crayon-s">'300'</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-75"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">gl</span><span class="crayon-sy">.</span><span class="crayon-e">viewport</span><span class="crayon-sy">(</span><span class="crayon-cn">0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">0</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-r">parseInt</span><span class="crayon-sy">(</span><span class="crayon-v">cvs</span><span class="crayon-sy">.</span><span class="crayon-v">width</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-o">+</span><span class="crayon-r">parseInt</span><span class="crayon-sy">(</span><span class="crayon-v">cvs</span><span class="crayon-sy">.</span><span class="crayon-v">height</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span><span class="crayon-sy">;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-76"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-r">setInterval</span><span class="crayon-sy">(</span><span class="crayon-v">render</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">16</span><span class="crayon-sy">)</span></div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-77"><span class="crayon-ta">&lt;/script&gt;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-78">&nbsp;</div>
                                <div class="crayon-line" id="crayon-57b2a5251fa58821350150-79"><span class="crayon-o">&lt;</span><span class="crayon-o">/</span><span class="crayon-v">body</span><span class="crayon-o">&gt;</span></div>
                                <div class="crayon-line crayon-striped-line" id="crayon-57b2a5251fa58821350150-80"><span class="crayon-o">&lt;</span><span class="crayon-o">/</span><span class="crayon-v">html</span><span class="crayon-o">&gt;</span></div>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
    <!-- [Format Time: 0.0291 seconds] -->
    <p> </p>
    <div class="addthis_toolbox addthis_default_style addthis_32x32_style" addthis:url="http://www.bswebgl.com/?p=415" addthis:title="WebGL Study 003 – Draw Triangle! (드디어 그려봅시다!) "><a class="addthis_button_facebook at300b" title="Facebook" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(59, 89, 152);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="Facebook" alt="Facebook" style="width: 32px; height: 32px;" class="at-icon at-icon-facebook"><g><path d="M22 5.16c-.406-.054-1.806-.16-3.43-.16-3.4 0-5.733 1.825-5.733 5.17v2.882H9v3.913h3.837V27h4.604V16.965h3.823l.587-3.913h-4.41v-2.5c0-1.123.347-1.903 2.198-1.903H22V5.16z" fill-rule="evenodd"></path></g></svg></span></a><a class="addthis_button_twitter at300b" title="Tweet" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(29, 161, 242);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="Twitter" alt="Twitter" style="width: 32px; height: 32px;" class="at-icon at-icon-twitter"><g><path d="M27.996 10.116c-.81.36-1.68.602-2.592.71a4.526 4.526 0 0 0 1.984-2.496 9.037 9.037 0 0 1-2.866 1.095 4.513 4.513 0 0 0-7.69 4.116 12.81 12.81 0 0 1-9.3-4.715 4.49 4.49 0 0 0-.612 2.27 4.51 4.51 0 0 0 2.008 3.755 4.495 4.495 0 0 1-2.044-.564v.057a4.515 4.515 0 0 0 3.62 4.425 4.52 4.52 0 0 1-2.04.077 4.517 4.517 0 0 0 4.217 3.134 9.055 9.055 0 0 1-5.604 1.93A9.18 9.18 0 0 1 6 23.85a12.773 12.773 0 0 0 6.918 2.027c8.3 0 12.84-6.876 12.84-12.84 0-.195-.005-.39-.014-.583a9.172 9.172 0 0 0 2.252-2.336" fill-rule="evenodd"></path></g></svg></span></a><a class="addthis_button_email at300b" target="_blank" title="이메일" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(132, 132, 132);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="Email" alt="Email" style="width: 32px; height: 32px;" class="at-icon at-icon-email"><g><g fill-rule="evenodd"></g><path d="M27 22.757c0 1.24-.988 2.243-2.19 2.243H7.19C5.98 25 5 23.994 5 22.757V13.67c0-.556.39-.773.855-.496l8.78 5.238c.782.467 1.95.467 2.73 0l8.78-5.238c.472-.28.855-.063.855.495v9.087z"></path><path d="M27 9.243C27 8.006 26.02 7 24.81 7H7.19C5.988 7 5 8.004 5 9.243v.465c0 .554.385 1.232.857 1.514l9.61 5.733c.267.16.8.16 1.067 0l9.61-5.733c.473-.283.856-.96.856-1.514v-.465z"></path></g></svg></span></a><a class="addthis_button_pinterest_share at300b" target="_blank" title="Pinterest" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(203, 32, 39);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="Pinterest" alt="Pinterest" style="width: 32px; height: 32px;" class="at-icon at-icon-pinterest_share"><g><path d="M7 13.252c0 1.81.772 4.45 2.895 5.045.074.014.178.04.252.04.49 0 .772-1.27.772-1.63 0-.428-1.174-1.34-1.174-3.123 0-3.705 3.028-6.33 6.947-6.33 3.37 0 5.863 1.782 5.863 5.058 0 2.446-1.054 7.035-4.468 7.035-1.232 0-2.286-.83-2.286-2.018 0-1.742 1.307-3.43 1.307-5.225 0-1.092-.67-1.977-1.916-1.977-1.692 0-2.732 1.77-2.732 3.165 0 .774.104 1.63.476 2.336-.683 2.736-2.08 6.814-2.08 9.633 0 .87.135 1.728.224 2.6l.134.137.207-.07c2.494-3.178 2.405-3.8 3.533-7.96.61 1.077 2.182 1.658 3.43 1.658 5.254 0 7.614-4.77 7.614-9.067C26 7.987 21.755 5 17.094 5 12.017 5 7 8.15 7 13.252z" fill-rule="evenodd"></path></g></svg></span></a><a class="addthis_button_compact at300m" href="#"><span class="at-icon-wrapper" style="line-height: 32px; height: 32px; width: 32px; background-color: rgb(255, 101, 80);"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 32 32" title="More" alt="More" style="width: 32px; height: 32px;" class="at-icon at-icon-addthis"><g><path d="M18 14V8h-4v6H8v4h6v6h4v-6h6v-4h-6z" fill-rule="evenodd"></path></g></svg></span></a><a class="addthis_counter addthis_bubble_style" href="#" style="display: inline-block;"><a class="addthis_button_expanded" target="_blank" title="더 보기" href="#">7</a><a class="atc_s addthis_button_compact"><span></span></a></a>
        <div class="atclear"></div>
    </div>
</div>
