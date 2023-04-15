# BoardPractice1
게시판 만들기 연습

list.jsp 페이지에서 다소 특이한 사항이 있었다.

$(function(){
								$('#searchBtn').click(function() {
									self.location = "list" + '${pageMaker.makeQuery(1)}' +
									"&searchType=" + $("select option:selected").val() + "&keyword=" +
									encodeURIComponent($('#keywordInput').val());
								});
							});
              
함수의 "&searchType=" + $("select option:selected").val() + "&keyword=" +
문단에서 오타로 "$searchType=" + $("select option:selected").val() + "&keyword=" +
를 적은적이 있었는데 그 때문에 검색기능이 정상적으로 작동하지 않았던 것이다.
문제는 신기하게도 엔터키를 눌렀을때는 정상적으로 검색이 기능했다는 점
검색버튼을 눌렀을 때에는 엉뚱한 URL로 연결해주던 기능이 아이러니하게 엔티키로 정상작동했다. 무슨 이유에서일지는 잘 모르겠다.

또한 BoardMapper.xml 단에서 페이징 구현 SQL문에 궁금한점이 있어서 ChatGPT로 알아보았다.

<!-- 게시판 리스트 갯수 -->
	<!-- 챗GPT의 설명 : 게시판 리스트 검색 쿼리문의 경우, CDATA 섹션이 없이 일반적인 SQL 문으로 작성되어도 문제가 되지 않습니다. 이는 쿼리문 내에 XML 문법에 영향을 줄만한 특수문자나 태그 등이 포함되어 있지 않기 때문입니다.
	그러나 게시판 리스트 갯수를 검색하는 쿼리문의 경우, COUNT 함수를 사용하므로, 결과값이 숫자형태로 반환되어야 합니다. 만약 CDATA 섹션이 없이 일반적인 SQL 문으로 작성한다면, SELECT COUNT(BNO) 구문에서 괄호나 대소문자 등이 XML 문법과 충돌할 수 있으므로, 
	CDATA 섹션을 사용해야 합니다. 이렇게 CDATA 섹션을 사용하면 SQL 문법 자체가 XML 문법에 영향을 받지 않으므로, 안전하게 SQL 문을 작성할 수 있습니다. -->
	<!-- 페이징구현까지 쓰던 mapper코드 -->
<!-- 	<select id="listCount" resultType="int">
		<![CDATA[
			SELECT COUNT(BNO)
				FROM MP_BOARD
			WHERE BNO > 0
		]]>
	</select> -->
  
	<![CDATA[   ]]>
  문을 쓰는 이유에 대해서 알아보았던 것이다.
  그 외의 특이한 이슈사항은 없다.
