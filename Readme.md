# Sourcelink란?
간략하게 소개하면 특정 코드만 Github, Gitlab, Bitbucket 등에서 다운받아서 디버깅 혹은, 내부 구현을 들여다 볼수 있는 기능

보다 자세한 설명은 아래 링크 참조
* https://github.com/ctaggart/SourceLink

## 이런분에게 도움됩니다.
* 내가, 혹은 팀원이 구현한 라이브러리에서 문제가 발생했는데, 라이브러리만 있고, 해당 코드는 깃에 있어서 다운받아야 할때!
* 내가 사용하는 라이브러리가 이 기능이 추가되어 있는데 불구하고 매번 Git 에서 해당 코드 검색 혹은 다운로드하는 분
* ASP.NET Core 2.0 source code를 디버깅 하거나 코드를 보고싶을때 (ASP.NET Core 외에 다른것도 가능하겠죠?)
 
<Strong> 왠만큼 유명한 라이브러리는 해당 옵션 추가될꺼로 예상</strong>

## Example!!

오픈소스 SourceLinkTest 를 다운받아서 SourceLinkTestClass 사용하는데, 10 + 20 값이 -10?? WT에프!!

![screenshot](https://raw.github.com/WhistlerHusky/SourceLinkTest/master/images/somethingwrong.png)

뭔가 잘못된게 확실한데??
(위 경우는 명백히 오픈소스에 문제가 있는거지만, 요즘 오픈소스를 많이 사용하다보니, 문제가 발생했을 경우 내 코드가 잘못된건지, 오픈소스가 잘못된건 분석해야 되는경우가 허다함!)

그래서 바로 저 Sum 함수가 어떻게 구현되엇는지 보고싶어서 F12를 누르면 보통은 아래와 같이 함수 선언부들만 나옴

![screenshot](https://raw.github.com/WhistlerHusky/SourceLinkTest/master/images/f12.png)

<B>여기서 만약 해당 라이브러리를 만든사람이 Sourcelink가 가능하게 해뒀다면, 해당코드를 바로 다운해서 디버깅 할껀지 Pop up 창이 나옴</B>
(두 컴퓨터에서 했는데, 하나는 팝업창 안나와서 아래와 같이 직접 설정해줘야 했음. VS 업뎃되면서 계속 뭔가 바뀌는듯)

https://github.com/ctaggart/SourceLink/wiki#sourcelinkcreatecommandline

![screenshot](https://raw.github.com/WhistlerHusky/SourceLinkTest/master/images/popup.png)

다운로드 Source and Continue Debugging 혹은 (Don't Ask Again) 클릭하면 아래와같이 해당 코드를 다운로드해서 디버깅 가능

![screenshot](https://raw.github.com/WhistlerHusky/SourceLinkTest/master/images/downloadedfile.png)

해당 파일이 다운로드된 경로.

![screenshot](https://raw.github.com/WhistlerHusky/SourceLinkTest/master/images/downloadlocation.png)

## ASP.NET Core 2.0 코드 debugging 해보기

아래 사이트 참조
http://laurentkempe.com/2017/09/26/Debugging-into-ASP.NET-Core-2.0-source-code/

## Sourcelink 지원되는 library(nuget) 만들어보기

![screenshot](https://raw.github.com/WhistlerHusky/SourceLinkTest/master/images/sourcelinkpackages.png)

1. Sourcelink 지원하고싶은 프로젝트에 위 2개 nuget 추가후 해당 코드 github 커밋
2. dotnet build /p:SourceLinkCreate=true /v:n 명령어로 컴파일

![screenshot](https://raw.github.com/WhistlerHusky/SourceLinkTest/master/images/dotnetbuild.png)

3. dotnet pack 명령어로 nuget file 생성!

![screenshot](https://raw.github.com/WhistlerHusky/SourceLinkTest/master/images/nugetpackage.png)

4. 생성된 nuget 파일을 테스트 하고싶은 프로젝트에 추가 후 테스트

만약 nuget 추가하는법 모르면 아래 링크 참조

https://stackoverflow.com/questions/10240029/how-do-i-install-a-nuget-package-nupkg-file-locally

참고 사이트

* https://github.com/ctaggart/SourceLink
* https://github.com/ctaggart/SourceLink/wiki#sourcelinkcreatecommandline
* https://stackoverflow.com/questions/10240029/how-do-i-install-a-nuget-package-nupkg-file-locally
* http://laurentkempe.com/2017/09/26/Debugging-into-ASP.NET-Core-2.0-source-code/












