### 진행순서 

1. 가장 먼저 github 가입

2. git bash 켜서

3. 순서 지켜서
   mkdir my_pyt
   cd my_pyt/                       (원래 이름은 pjt / 오타난 것)
   touch .gitignore
   touch README.md      touch .gitignore README.md
   
   구글링 : gitignore - pycharm - ignore 파일에 내용 저장 
   <img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618113619290.png" alt="image-20210618113619290" style="zoom:50%;" />
   
4. 파이참 open (init보다 이게 먼저! 꼭 순서!)
   해당 폴더 안에 파이참 오픈해서
   `.gitignore`  안에 적어야 하는 내용 구글링

5. 구글 - gitignore-gitignore.io
   그 안에 windows, python, macOS, 등등

   생성- 안에 나오는 내용: ctrl +a, c, v(파이참 이그노어 안에)
   (init보다 이 순서들 중요)
   이렇게 무시할 거 다 무시시키고

<img src="013.assets/image-20210607040359422.png" alt="image-20210607040359422" style="zoom:80%;" />  

6. git init	(카메라 )
   git add . (모두 올려 보내고)

![image-20210618114126894](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618114126894.png)

<img src="013.assets/image-20210607040427677.png" alt="image-20210607040427677" style="zoom:80%;" /> 

[git add .] 했는데 "LF"로 시작하는 워닝나오면 무시 가능함. 
10여 개 나오는 건 가능하지만, 몇 만 개 나오는 건 문제 있는 거니깐, 그 땐 한 번 체크! 

<img src="013.assets/image-20210607040516368.png" alt="image-20210607040516368" style="zoom:80%;" /> 
[git add .]한 후에는 'enter' 하나도 캐치를 해낸다. 
그만큼 sensitive하다. 



### 1. commit - vim

<img src="013.assets/image-20210607041001608.png" alt="image-20210607041001608"  /> 

오타 수정만 몇번째야… 그냥 이전 commit에 포함하면 안되나? 
그래서 [git commit - - amend] 하면.... 으악 이상한 창이 뜸. 

  - git commit --amend
    가장 최근에 commit한 내용이 포함되어 있을 거다.
    그래서 최근 commit 을 수정하고 저장하고 빠져 나오는 거다. 

<img src="013.assets/image-20210607041837294.png" alt="image-20210607041837294"  /> 

이런 거 나오면 건들지 말고 일단 
여기서 잠깐 [파이썬] 두고, [git bash]를 켜자. 



#### 1-1. touch & modify[git bash]

[git bash] - "touch a.txt" 

a.txt를 수정해야 하는데 git bash를 벗어나서는 안된다고 하면 어떻게 하면 될까? 문서 편집하는 방법은? 이 때 쓸 수 있는 편집기가 'nano'  'emacs'  'vim' 3가지가 있음(각각 sw이름) 
여긴선 major인 vim을 사용하자

<img src="013.assets/image-20210607042412081.png" alt="image-20210607042412081" style="zoom:45%;" /> 

##### 1) touch & vim

​	$ touch a.txt
​	$ start a.txt
​	$ vim a.txt
​	$ vim

어떤 창이 뜨는데, 거기에 'z'치면 입력이 안 돼.
**커멘드 모드**에서는 입력이 안 돼.

##### 2) insert & wq

입력하기 위해선 **[ i ]** 입력 : 하단에 **insert** 생성 
**[esc]** 누르면 insert 사라짐.

<img src="013.assets/image-20210607043017216.png" alt="image-20210607043017216" style="zoom: 80%;" /> 

입력다하고는 ? [저장] - [종료]
[esc] - [저장 = :w (명령한다, 쓴다) + enter(저장)]
실제 파일 열어보면 수정된 걸 확인할 수 있음. 

그러면 vim을 끈다고는 어떻게 하지?
[esc]-[:q]

**저장과 종료**를 한 방에 할 수는 없을까?  [esc]-[:wq]

##### 3) 강제종료 :q!

그럼 반대로 저장 안 함!은 어떻게 할까? [:w] 없이 [esc]-[:q] 입력하면 작동 안 함. 그럴 땐 꺼! 라고 얘기하면 꺼집니다. 
[esc]-[:q!]  : 이렇게 하면 저장 안 하고 끈 것입니다.



#### 1-2. 덮어쓰기 [Python]

오타 수정만 몇번째야… 그냥 이전 commit에 포함하면 안되나? 
그래서 [git commit - - amend] 하면.... 으악 이상한 창이 뜸. 

<img src="013.assets/image-20210607041837294.png" alt="image-20210607041837294" style="zoom: 80%;" /> 

이건 우리가 켜달라고 하지도 않았는데 vim을 켜준 상태에서 얘기 중. 

> 아까 first commit 했는데 여기에 편입시키려 할 때, 
> 편입은 하게 해줄 건데... 혹시 commit 메시지 변경 원해? 

##### 1)  메시지 변경 없이 덮어쓰기 

그런데 원하지 않아, 그러면 ? 
[esc] - [:wq] 그 후에 [git log] 확인하면 'first commit'은 그대로 있지만 방금 편집한 내용이 포함 된 걸 확인할 수 있다. 

##### 2) commit 메시지 수정 후 덮어쓰기

메시지 고칠 때도 역시 [git commit - - amend] 하면 `마지막 최종 commit에 수정`사항을 위해 vim 작동 : [ i ] - [수정] - [esc] - [:wq] - enter
하고 git log 보면 메시지 바뀐 것을 확인할 수 있음 

###### 		cf. [esc] 팅김

​			[esc] 누르면 계속 파이참 위로 팅길 경우
​			[ctrl+alt+s] - [keymap] - [오른쪽 검색: terminal] - 
​			맨 밑[escape] - 우클릭 지우기 [remove]-[ok]

######				cf. git commit -m / 

​			하고 메시지 작성하지 않으면? 똑같이 vim으로 넘어가게 됨 

  

### 2. commit - master

다시 시도 "touch main.py" 
파이참에서 [프로젝트] 창 밑에 있는 [commit]을 통해서도 commit 가능

▶ 그러면 지금 커밋 2개 
▶ first commit
	백지에 commit 점을 찍는 것 

![image-20210607050357343](013.assets/image-20210607050357343.png) 

백지에 먼저 first commit이 생김 (빅뱅이론 느낌)
거기에 메시지를 넣은 것 "first commit"
여기에 main.py 추가, 그런데 여기서 master라는 게 생기는 데 이 의미는 뭐지? 

#### 2-1. master 

마스터는 **`이 중에서 최고`**라는 뜻 

<img src="013.assets/image-20210607050606923.png" alt="image-20210607050606923" style="zoom: 80%;" /> 

#### 2-2. head

그러면 head는? "나 여기에 있소!"라는 의미, 노란색 지표! 
[나의 머리, 내가 보고 있는 곳, 이 시점에 있소!]

![image-20210607050729364](013.assets/image-20210607050729364.png) 

#### 2-3. checkout - master vs head

그런데 master랑 head가 각각 다른 곳에 있을 수 있나? Yes. 
만약 checkout 하면 head만 다른 곳에 가 있음.  / checkout 51f2 이런 식으로 
즉, 내가 있는 시점은 여기(head)이고, master는 다른 곳에 그 시점에 멈춰 있는것. 

$ git checkout master 하면? 
내가 있는 시점에서 checkout 해서 마스터로 향하는 것. 
즉, checkout은 시간이동. head를 움직이는 구나!



#### 2-4.  중급의 시작: master

그럼 이 중의 최고라는 master는 좀 더 정확히 뭘까? 
이걸 branch 라고 한다. 중급의 시작. 
[ head -> master ]의 의미는 "현재 나는 master branch(가지)에 있다."

여기에 새로운 파일을 add / commit 한다면
commit = 이어지는 거니깐 연결 될 거고, 
마스터 화살표가? 다음 점으로 넘어갔다.

<img src="013.assets/image-20210607051819882.png" alt="image-20210607051819882"  /> 이게 commit이고, 이게 branch  !

※ master = 화살표이다!
master branch 는 한 줄로 이어지는 것? 아님! 
이 가지들 중에서 마스터 가지는 **하나**, 그걸 화살표로 표시하는 것임

 

### 3. 실험적인 코드 : 나 다시 돌아갈래

코드를 쓰다가 망해서 다시 처음부터 하려고 한다면? 
$ git restore main.py
이러면 마지막 commit 시점으로 돌아간다. 

그런데 한달 정도 지속한 상황에서 돌아가려고 하면? 
한달간 commit을 안해야 한다? 아니다. 

그럼 10~20개 commit이 쌓였는데 과거로 돌아가면 되나? 아니다. 

![image-20210607052730148](013.assets/image-20210607052730148.png)

이걸 예로 들면 
파이선에서 작성한 [ print('master branch') ] 이것만큼은 꼭 돌아야 하는 기능이라고 하면 [ print('master branch') ] 는 그대로 원본에 두고 복붙해서 다른 기능을 추가하는 … 다른 **평행세계**에서 굴리면 되지 않을까? 라는 생각이 든다. 

#### 3-1. git branch

<img src="013.assets/image-20210607053119639.png" alt="image-20210607053119639" style="zoom:80%;" /> 

지금 이 상태를 그림으로 표현하면 (실제로 할 땐 영어로!)

![image-20210618114951349](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618114951349.png) 

![image-20210607053154015](013.assets/image-20210607053154015.png)   ![image-20210607053519766](013.assets/image-20210607053519766.png) 
여기서 점(commit)을 찍으면 안 된다. 그냥 branch 하나가 뻗어 나오고 있는 중인 상태이다. 평행세계가 시작되려는 단계

![image-20210618115050236](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618115050236.png) 

![image-20210618115151831](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618115151831.png) 

<img src="013.assets/image-20210607053345742.png" alt="image-20210607053345742" style="zoom:80%;" /> 

#### 3-2. git switch

여기서 **[git switch 실험]**이라고 치면
![image-20210607053519766](013.assets/image-20210607053519766.png) ![image-20210607053955469](013.assets/image-20210607053955469.png) 
**노란색 지표(head)**가 master에서 **실험**으로 바뀜! 

여기서 [git log]치면 (head -> 실험, master)라고 뜸. 
지금 새로운 세상이 뻗어 나가려고 하는데 커밋이 없다 보니깐
(git은 '커밋'만 생각하는 바보다. 그래서 '커밋'이 없다보니)

![image-20210618123420261](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618123420261.png) 

<img src="013.assets/image-20210607053548366.png" alt="image-20210607053548366" style="zoom:150%;" /> 

##### cf. **switch & checkout**

 * 여기서 잠깐, 
   **$ git switch master** 라고 하면 어떻게 될까?
   아마, **head가 master**를 가리킬 것 같다.  딩동댕!
   switch가 branch를 이동할 때 사용하는 명령어 같다! 

![image-20210618115307236](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618115307236.png) 

 * 어라? head 이동하는 명령어 있었는데? 
   checkout / 그래서 똑같이 움직인다. **switch & checkout**
 * 참고로 switch는 최근에 등장. 원래는 제작년만 해도 checkout만 있었음.
   **머리움직이는 checkout **: 앞뒤, 과거 현재, 다른 세상 오갈 수 있음. 
   여기서 업데이트 할 때 이동하는 게 달랐으면 좋겠어서 switch를 만듦. 

#### 3-3. 평행세계의 시작 : commit

 * 하여튼, 평행세계 시작을 만들려면? commit을 해야 합니다. 

##### 1)  head 위치 

[git status] 확인해서 '실험'에 head가 있는 거 확인하고 
[git switch 실험]

##### 2) add - commit : 평행세계 생성 

- 변경한 파일 저장하고 
- 이 상태를 저장 후 촬영하면 (add - commit)
  이제 평행세계가 생긴 것. 

<img src="013.assets/image-20210607054906053.png" alt="image-20210607054906053" style="zoom:67%;" /> 

##### 3) git log

여기서 git log를 확인하면 master는 다른 공간에 있고, head(지금 나 여기 있소!)는 실험을 향하고 있는 상황을 확인 할 수 있다. 

<img src="013.assets/image-20210607054936330.png" alt="image-20210607054936330" style="zoom:80%;" /> 

이걸 그림으로 그리면 아래와 같다. 
마스터의 시간은 멈춰 서 있고, 실험의 시간은 현재로 움직이고 있는 거다. 



<img src="013.assets/image-20210607055040810.png" alt="image-20210607055040810" style="zoom:60%;" /> 

##### 4) git switch master

여기서 git switch master하면 어떻게 될까? 
		1) head가 움직임. 
			이제는 시간이 동시간대에 흐르는 것이 아니라 다른 시간에서 흐르는 것. 

​		2) 코드가 사라진다. 그런데, 사라진 게 아니다. 
​			지금 이 시간에는 이 코드밖에 없는 것. print('master branch')만. 
​			시간이 두가지로 나뉘어 있을 뿐이다. 이것이 바로 브랜칭의 핵심.

![image-20210607052730148](013.assets/image-20210607052730148.png)

​			그래서 실험을 할 때, 망하면 master로 돌아오고, branch를 폐기하면 됨.
​			master도 계속 실행이 잘 되고 있어야 하고. 
​			그런데 만약에 실험이 성공했을 때는 ?
​			[지금 이 상황들이 branching의 핵심이다.]



![image-20210618123924358](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618123924358.png) 

![image-20210618123950369](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618123950369.png) 

![image-20210618124024991](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618124024991.png) 

![image-20210618124057134](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618124057134.png) 

마스터로 가면 실험 내용 없음 



![image-20210618124320683](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618124320683.png)  

![image-20210618124431609](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618124431609.png) 

![image-20210618124515049](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618124515049.png) 

![image-20210618124534835](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618124534835.png) 

![image-20210618124621135](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618124621135.png) ![image-20210618124640282](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618124640282.png) 

![image-20210618124707879](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618124707879.png) 이렇게 움직여야 한다. ![image-20210618124746073](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618124746073.png) 

![image-20210618125333766](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618125333766.png)  



![image-20210618125101517](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618125101517.png) 

![image-20210618125143126](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618125143126.png) 

 ![image-20210619033432988](013.assets/image-20210619033432988.png)  

- branch에서 할 일이 끝났다면 : 저장 - add - commit
- master로 간다. git switch master
- merge 한다. git merge dev
- branch 지운다. git branch -d dev

![image-20210618145523416](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618145523416.png) ![image-20210618145544669](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618145544669.png)

![image-20210618125727990](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618125727990.png) 







### 4. conflict

![image-20210619033502960](013.assets/image-20210619033502960.png) 이런 상황이 궁금해 

#### 4-1. 첫 번째 충돌

![image-20210618125751142](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618125751142.png) 

[ git switch -c test ] 이렇게 사용하면 
[ git branch test + git switch test ] 를 한 번에 사용하는 꼴임. 

​	branch 생성 + switch 이동 

![image-20210618125855686](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618125855686.png) 

![image-20210618125944658](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618125944658.png) 

![image-20210618130159058](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618130159058.png) 

![image-20210618130212015](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618130212015.png) 

> 개발하는 도중에 master는 계속 움직이는 중 
> 그런데 master 문제 생겼다 하면 
>
> 1) switch master. 
> 현재 master. 
> 파일 하나 더 필요하겠는데? 
> 2) touch sos.py
> 3) 내용 수정
> 4) add & commit  

실제 이런 상황 / log 치면? 이제 진짜 평행세계 
master - log
new - log 		두 가지가 완 전 다른 세상. 

![image-20210618130352123](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618130352123.png) 

![image-20210618130410794](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618130410794.png) 위와 같은 상태에서 새로 커밋하면 ? 

![image-20210618130528529](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618130528529.png) 

여기서 다시 커밋을 만들면

 ![image-20210618130717772](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618130717772.png)  ![image-20210618130946329](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618130946329.png) 

이제 아예 다른 길을 걷는 중. 
나중에 이걸 합쳐야 할 텐데 어떻게 합치지? 
마스터가 옯겨 가면 되는데 브랜치가 두 가지인 상황에서 어쩌지... 

![image-20210618131044875](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618131044875.png) 

이렇게 마스터가 옮겨간다면 (merge) 
sos는 어떻게 하지? 이 상태는 sos가 허공에 사는 거다. 

이럴 때 정말 sos도 반영해서 다 병합할 수 있을까? 사실 똑같다. 명령어는.
그런데 그 모양을 이해해야 한다. 저 물음표 안에서 일어나는 일을 이해하자. 

![image-20210618133846626](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618133846626.png) 

switch master 하면 new 내용 사라짐! / 진짜 사라지는 게 아니고 .
git merge new. 마스터가 뉴랑 합체하겠습니다. 

![image-20210618134059762](013.assets/image-20210618134059762.png) 

그랬더니 vim이 뜸. 갑자기. 
vim 뜨는 상황은 amend랑 커밋 메시지 넣으라고 할 때. 2가지 뿐인데. 
여기서도 마찬가지로 commit 메시지 달라는 것. 
병합하는 이유를 적으라는 것인데 ... 쓰나 마나 편할 대로. 

![image-20210618134031684](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618134031684.png)  

 :wq 하고 나오면 뭐라고 뜨는데 
그게 중요한 게 아니고 이렇게 merge 끝난 거고 
오른 쪽에 보면 new feature도 있고, sos feature도 있는 상황 
결과는 원하는 대로 됐는데 이게 중요한 게 아니다. 

이게 어떻게 된 그림인지 추측해보자. 
아까 commit 메시지 창 떠서 뭐 어쨌든 commit을 했는데. 

그러면 그 commit은 점을 어떻게 찍어야 할까
[ Winner takes all : 하나밖에 안남는다. ] 
master로 오고, 머지 하고, 커밋 [점]까지 했다. 그 커밋은 마스터의 커밋.

그걸 그리면 아래와 같다. [ 합체 ]

![image-20210618134422861](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618134422861.png)  

참고로 아래  처럼 파이참에서 git merge를 할 경우엔 알아서 결과가 나온다. 
git bash는 나한테 다시 물어본 것 

![image-20210618134304166](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618134304166.png) 

![image-20210618134621131](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618134621131.png) 

쪼개진 세상이 한 눈에 안들어온다. 그래서 decorate

![image-20210618134746680](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618134746680.png)







위에서 두 점을 합치는데 너무 스무스하게 넘어갔다. 그 이유는 ? 

![image-20210618150003376](013.assets/image-20210618150003376.png) 

수정한 게 어떤 거면 
모두가 똑같은 상황은, main.py가 있고 그 안의 내용이 노란색 만큼 있었는데 
빨간색 뉴의 커밋은 main 안에 코드를 추가한거 였다. 

파란색은 sos.py 만들어서 넣은 거다. 둘이 색깔만 봐도
겹치는 곳이 없다. 빨간 색이 있는 곳과 파란 색이 있는 곳에 겹치거나 
영역을 침범하지 않는다. 왜 ? 전혀 다른 파일이고 다른 파일의 줄이니깐. 

그럼 겹치면 어떻게 되는데? 

저기 위의 1.2.3.4 한 거고 new 지워줘야 한다. 
또 새로 만들 수 있지. 이름만 안 겹치면 돼 

![image-20210618150020424](013.assets/image-20210618150020424.png) 

그러면 이런 느낌으로 다시 나아가야 하는 거다. 남기는 게 아니라.
branch -d <>



#### 4-2. 두 번째 충돌: level up

- master

- git swirch -c my-brench 하고 내용 작성 

  ![image-20210619032358052](013.assets/image-20210619032358052.png) 

   

- git add . && git commit -m "sos.py => change"

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618150331129.png" alt="image-20210618150331129" style="zoom:80%;" /> 

두 영역이 서로 침범하는 시나리오를 찾아 가는 중.

- 마스터에서 아래 내용 작성 

![image-20210619032415298](013.assets/image-20210619032415298.png) 

여기서 마스터의 이름으로 명하노니 merge 하라!? 가능?

내용이 전혀 다름. 아까 처럼 서로의 영역을 전혀 침범하지 않는 상황과는 다름
확연히 침범 중. 첫 줄도 다르고, 줄도 다르고, 내용도, 이름도 다 달라. 완전 충돌. 

일단 변경 내용 저장. add & commit 
마스터에 있다. 그런데 마스터에 있는 게 중요한 게 아니라 
서로 다른 브랜치라는 것이 중요 

![image-20210619032619304](013.assets/image-20210619032619304.png) 

여기서 merge하면 어떻게 될까? 
1) 같이 사이 좋게 살자, 둘 다 쓰자.
	둘 다 로그인 짰는데. 그걸 같이 평화롭게 쓰면 로그인 2개

2) 마스터가 쌔니깐 마스터꺼로 가자. 
	더 좋은 게 있을 수 있는데 덮으면 속상해. 

우리가 진짜 원하는 건? 이 난처한 상황에서. 

![image-20210618151703558](013.assets/image-20210618151703558.png) 

충돌 났어 너가 고쳐 그리고 커밋해. 
그래서 여길 가보면. 

![image-20210618151323885](013.assets/image-20210618151323885.png) 

이렇게 줍니다...ㅋㅋㅋㅋ 

> <<<<<< HEAD .. 여기가 헤드 부분이고 
> =================... 이렇게 나눠서 
> *>>>>> my-branch .. 여기가 브랜치 부분이야. 

이렇게 찍찍 그어서 줌. ㅋㅋㅋ 난해해.. 니가 알아서 해 
님이 알아서 하세요. 하고 도망 / 이건 구현이 안돼. 
그러면 ? **수동으로 고쳐**서 저장해야 하는 거다. 

진짜 이렇게 / 수동 수정. 저장. add. commit.

근데 여기서 끝이 아님. 

![image-20210618151703558](013.assets/image-20210618151703558-1624041915519.png) 

수정만 하고 commit 안 한 상태가 이 상태. / 점 안 찍힌 상태. 

![image-20210618151721644](013.assets/image-20210618151721644-1624042165545.png) 

이 브랜치의 이유가 
수정했다 자체보다 머징과정이라 
커밋메시지 글씨 색깔 다른 걸 알 수 있다. 





### 5. remote : 외진, 외딴, 먼  (git & github)

![image-20210618162031373](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618162031373.png) 

![image-20210618164122474](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618164122474.png) 

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618164655369.png" alt="image-20210618164655369" style="zoom: 67%;" /> 

우리는 이미 README와 gitignore 둘 다 갖고 있는 상태라 클릭 안해도 돼. 

![image-20210619044526609](013.assets/image-20210619044526609.png) 

create  a new (local) repository on the command line. 이라고 읽자. 
그런데 우리는 이미 파일이 있어! 그러니깐 existing으로. 
그런데 못보던 게 있다. [git branch -M main] ... 이건 그냥 지워버려도 돼

마스터 대신에 이름을 main으로 하는 거 어때? 라는 얘기임. 
main 직관적이고 좋네. 흑인 master slaves를 떠올린다 해서 바뀐 거임 / 정치적 올바름 바람

anyway

- git remote add origin <URL> : 이게 화살표 지정하는 거고
- git push -u origin main : 이게 업로드 하는 거
  그렇지만 우린 이걸로 사용하지 않겠다. 

<img src="013.assets/image-20210619045247525-1624045970967.png" alt="image-20210619045247525" style="zoom:80%;" /> 

- 1번 완료
- 2번 : 화살표 지정 + 이름 지정 (할 차례) ... 파이참이든, 터미널이든 ok
  git remote add <이름> <url>
  remote repo를 local repo에 추가합니다. 뭐라고 부를 거구요. 인터넷 주소.
  ![image-20210619045804256](013.assets/image-20210619045804256.png) 
  git remote add origin https://github.com/lovegohome/remote-repo-example.git
  그러고 파이참은 ctrl + v / git bash는 우클릭 paste or insert key + shift
- git remote -v 
  remote의 버전을 보여주는 것. / 2개가 나오지만 1개임. upload, download.
  그리고 여기에 위 주소를 더 추가 할 수 있음. 여러개 가능. 
- git remote remove <이름>
- git remote -v 
- git remote add <이름> <URL> : 이게 화살표 지정하는 거고
- git push <이름> <브런치> 
  이름 붙힌 주소로 보내줘, 그런데 master brench 안에 있는 내용만 올려줘. 
  라는 뜻임. 그래서 만약 branch Yoojung에서 올릴 거라면 master가 아니라 
  git push origin Yoojung 이렇게 씀.
- github sign in with your browser
  누르면 appented succed? (13-5 끝부분인듯)



#### 5-1. git remote

- git remote가 바로 원격 저장소를 관리할 수 있는 명령어입니다.
- git remote add <부를 호칭, origin> <호칭 부르면 들어갈 URL 주소> 
- git remote -v  로 주소를 확인해준다. 
- git push <정한 호칭, origin> <브랜치>



### 6. 두 컴퓨터에서 push 

- mkdir algorithms

- cd algorithms/
  만들어진 거 체크

- cd .. 
  상위로 다시 올라간 상태에서 add를 하네?

- git add . 

- git commit -m 'new dir'
  그럼 여기서 nothing to commit 뜸. 
  비어있는 파일은 인식을 못하기 때문, 알고리즘 폴더 안에 뭔가를 만들어야 돼. 

  그냥 그 안에 다른 폴더 넣어도 됨 

- 그러고 나서 add & commit 
  후에 push <리모트 이름> <브랜치>

![image-20210621101659596](013-ing.assets/image-20210621101659596.png) 

- 현재 이 상태. 그런데 두 컴퓨터에서 올리려고 하면? 
  충돌 생김 

- 집 말고 강의실

  ![image-20210621102105180](013-ing.assets/image-20210621102105180.png) 

  git remote add <이름> <url>
  git push <리모트이름> <브랜치>
  그 url 중 어디로 보낼지. 

- 강의실(B컴)에서 깃허브에 같이 올리려고 할 때 / 
  먼저 TIL을 받는 게 우선이다. 받는 것 : Clon

  1) 여기서 주소 복사
  ![image-20210621103201304](013-ing.assets/image-20210621103201304.png)
  클로닝? 

  DNA **클로닝**(DNA **Cloning**)은 유전 공학의 기법 중 하나이다. 조작한 DNA를 세포에 도입하고 복제하는 과정을 거쳐, 무수히 많은 DNA 사본을 얻어내는 기법이다.

  cf. 크롤링
  **크롤링**(crawling) 혹은 스크레이핑(scraping)은 웹 페이지를 그대로 가져와서 거기서 데이터를 추출해 내는 행위다. 

  2) 클론 뒤에 그 주소 넣으면 됨 (B컴)
  ![image-20210621103539158](013-ing.assets/image-20210621103539158.png) 

  3) ls -a 하면 아래 링크, 그리고 넣고 싶은 폴더 확인  
  ![image-20210621103724597](013-ing.assets/image-20210621103724597.png) 

  4) cd TIL 
  <img src="013-ing.assets/image-20210621103832618.png" alt="image-20210621103832618" style="zoom:55%;" />

  (아마 여기서 강의 중에 말씀은 안하셨는데 카메라 설치해야하는 듯 )
  (왜냐면 뒤에서 status 사용)
  (음? 카메라 없이도 status 가능한가?)
  (일단 패스 )

  

  그러면 현재 
  ![image-20210621103912538](013-ing.assets/image-20210621103912538.png) 

  이런 느낌으로 하나의 인터넷(리모트)에 두 개의 local(집, 강의장) 연결 된 것. 

  5) B컴에 파일 만들고
  mkdir python
  cd python
  touch variable.py.md
  cd TIL
  git status, add, commit. 

  - 여기서 우리는 드디어 뭔가를 한 거다. 
    commit의 로그가 달라졌을 거다! 
    (생각은 커밋 단위로!)
  - git log --oneline
  - <img src="013-ing.assets/image-20210621105244387.png" alt="image-20210621105244387" style="zoom:55%;" />
  - 새로 본 애들이 생김 
    origin/master, origin/head
  - head -> master 
    로컬의 마스터 브랜치에 있다는 거
  - origin = 인터넷. 
    오리진의 마스터 브랜치도 여기에 멈춰
    오리진이 현재 보고 있는 것도 여기에 있더라(?)

  6) 강의장에서 집으로 향할 때 해야 할 일 

  - git push origin master 
    그럼 이전과 이후의 변화를 생각해봐야 할 때. 
    그러면 python 폴더 올라갈 건데 +a
    log 찍으면 어떻게 변할까? 
    origin/master, origin/head 이 두개가 위로 올라감. 아까는 한 단계 뒤에 있었다. 왜? 이 변경 내용은 B컴에서 한 게 아니야. 그런데 push 하는 순간 싱크가 맞은거죠. 내 컴퓨터의 최신도 여기 있고 저 멀리 있는 리모트의 최신도 여기 있고

  6-1) push 후 
  <img src="013-ing.assets/image-20210621105505932.png" alt="image-20210621105505932" style="zoom:55%;" /> 

  실제로 확인 가능. 

  <img src="013-ing.assets/image-20210621105723214.png" alt="image-20210621105723214" style="zoom:70%;" /> 

  이제 싱크가 맞는 건 
  여기서 이제 강의장(B)랑 인터넷이랑 싱크가 맞은 것. 

  * push 없이, commit만 한 경우는 
    a(2)-remote(2)-b(3)  :  commit 수 
  * push 한 후에는 
    a(2)-remote(3)-b(3)

  그런데 여기서 집(A)는 싱크가 안 맞음. 피곤하지만 공부를 해야겠다. 그걸 배워보자 .

  9) 보내는 게 push 였는데, 
  B 컴퓨터의 내용을 보냈잖아, 그걸 A가 받아야 돼. 
  받을 때 PULL. 
  ![image-20210621115127348](013-ing.assets/image-20210621115127348.png) 

   A는 받아야 하는 상황 

  - git pull origin master   : 여기선 master에서 땡겨오는 것 

  - ls 로 들어온 거 봐도 되고 

  - git log --oneline으로 봐도 커밋 3개 된 걸 확인 가능 
    이 때 모든 싱크가 맞은 상태 

  - 집에서 또 공부한다고 하면 
    touch python/01_operator.py
    mv python/01_operator.py/01_operator.md  : 저걸 이렇게 바꾼다? 
    move가 파일을 이동하는 거였는데, 확장자를 바꾸면? 이름을 바꾸면? 
    이름이 바뀌어요. / 이건 설명 생략 나중에 찾아보세요. 

  - 그럼 거기서 git status 치면 
    ![image-20210621120305017](013-ing.assets/image-20210621120305017.png) 
    이거 처음 본다고 뜨고 

  - 거기서 add & commit 

    - 그리고 log 찍으면 
      ![image-20210621120404565](013-ing.assets/image-20210621120404565.png) 
      나는 한 스탭 더 나간 상태가 된다. 즉 저 3이 아니고 4가 되는 상태 
      ![image-20210621120813493](013-ing.assets/image-20210621120813493.png) 

    - 아 공부 다 했다. 자야지 ...  ? 

      잠들기 전에 해야 할 건 ?  push! 

    - git push origin master. 
      ![image-20210621121417815](013-ing.assets/image-20210621121417815.png) 

    - 다음 날 강의실 가면? 
      git pull origin master 

    - 즉, sit - pull / stand - push 
      집에 앉아서, 강의장 앉아서  pull
      일어나면서 push

    - 그런데 이건 혼자서 두 컴퓨터 쓸 때의 일이다. 
      remote가 한 컴퓨터 보다는 늘 늦어지게 되는데.
      ![image-20210621121745747](013-ing.assets/image-20210621121745747.png) 

    - 협업을 하게 되면 remote가 앞서 나아가게 된다. 
      먼저 치고 나가는 시점이 생김 / 개인보다 팀이 쌤. 
      ![image-20210621122424914](013-ing.assets/image-20210621122424914.png)

      개발자 A, B  /  TEAM
      그래서 TEAM의 결정사항을 A,B가 따르게 됨 
      그리고 코드가 부딪히면 A,B가 결정하는 게 아니라 TEAM이 결정하게 됨

      TEAM이 우리 프로젝트의 근본이 되고, origin이 된다.

      ![image-20210621122654444](013-ing.assets/image-20210621122654444.png) 



### 7. TEAM으로 PJT, 협업

#### 7-1. remote에 새 창부터 

![image-20210621122842724](013-ing.assets/image-20210621122842724.png) 

이건 팀원이 모두 만드는 게 아니라 1명이 대표로 만듦. 

그리고 아직 우리에겐 README, .gitignore 없음 

![image-20210621123352178](013-ing.assets/image-20210621123352178.png) 

- 이그노어는 나중에 수정

- 여기서 좀 나쁜 게 뭐냐면. 

  This will set main as the default branch.
  라고 되어 있는데ㅡ 이거 세팅하는 순간 main branch를 강제시켜버린다. 
  그리고 세팅가서 메인을 바꾸래. 

  main을 master로 바꿀 수 있습니다. 취사선택.

  근데 지금 우리가 branch를 자유자제로 쓰면 모르지만 처음에는 익숙하지 않으니깐 지금까지 한 걸로 하겠다. 

  바꾸려면 세팅 - 아래처럼 update
  ![image-20210621123940193](013-ing.assets/image-20210621123940193.png) 

  바꿨으면 돌아가서 create 누르기. 

#### 7-2. remote에 먼저 pjt가 만들어졌고 그걸 A,B개발자가 

각각 받아야 하는 상황 

![image-20210621124105885](013-ing.assets/image-20210621124105885.png)  

- X : git clone <url>

  이렇게 하면 안돼 . 
  아까는 이렇게 했지만 지금은 협업.
  저렇게 쓰면, 자동으로 이 이름으로 폴더를 만들려고 한다. 

  이렇게 만약에 한다고 하자, 그러면 refo를 받았는데 refo = folder (근본)

  그럼 그 받은 folder 이름이 뭘까?
  무슨 이름으로 받았을까? 그 이름 대로 받음 
  ![image-20210621124856159](013-ing.assets/image-20210621124856159.png) 

  ![image-20210621124927306](013-ing.assets/image-20210621124927306.png) 

- 그런데 여기서 문제는 이걸 A, B 둘 다 받을 텐데. 폴더 명이 똑같아. 충돌

  그래서 이름을 바꿔서 받음 
  <img src="013-ing.assets/image-20210621125309158.png" alt="image-20210621125309158" style="zoom:67%;" /> 

  즉, git clone <url> <다른 이름>

- 하지만 그 내용은 동일함. 
  cd A_team_pjt
  ls

#### 7-3. 그렇게 A,B 모두 만들면 상황은 

![image-20210621130020033](013-ing.assets/image-20210621130020033.png) 
아까 말한 TEAM의 우위 차지가 왔다. 
혼자 2 컴퓨터 쓸 때는 1-0-0 이었는데 
팀으로 할 때 0-1-0 상태에서 시작. 

그래서 팀이 우선하는 상황이 오는 것임. 
이렇게 팀이 우선되는 상황이 오기도 해요. 

#### 7-4. 세팅은 완료했고, 

혼자 사용할 때는 굳이 branch를 사용하지 않았는데 여기선 사용해야 된다. 
브랜치를 안쓰면 아주 고통스러운 상황이 온다. 

우리 마스터에 하자? 하면….
A의 역할: home.html
B의 역할: about.html

BOTH: 둘 다 readme에 한 내용 적기 (done) 

#### 7-5. A에서의 작업

- A에서 파일 만들고 readme 작성
  ![image-20210621131101662](013-ing.assets/image-20210621131101662.png) 

  (cf. html은 파일명)

- ![image-20210621131213514](013-ing.assets/image-20210621131213514.png) 
  <img src="013-ing.assets/image-20210621131257384.png" alt="image-20210621131257384" style="zoom:50%;" />  
  cf. 이건 a에 있는 리드미
       b에 있는 리드미 완전 달라.

  내가 한 거 적어. **파일 저장**(ctrl+SSSS)하고.

- add & commit

- git push origin master 
  master로 한다면 생길 상황들을 이제 보자! 
  ![image-20210621131554361](013-ing.assets/image-20210621131554361.png) 

#### 7-6. B에서의 작업

- touch about.html

- start README.md

- B의 README는 다른 것!!! 
  ![image-20210621151444968](013-ing.assets/image-20210621151444968.png) 
  내가 한 거 작성
  .md 저장저장저장

- B라고 한다고 다음인지 모르는 것! 
  이거야 이름일 뿐. 실제로는 순서 몰라. 

- 여튼, add & commit 

- 했으니깐 나도 올려야지 
  git push origin master 
  (당연히 얘 입장에선 이게 맞지. 나 일 했으니깐 push할 게! ...... 으악)

  ![image-20210621152354570](013-ing.assets/image-20210621152354570.png) 

#### 7-7. error 문 왜 나왔을까여? 

- 같은 파일에 내용이 달라서? 아니다. 
  같은 줄에 다른 내용이라는 건 충분히 합리적인 의심이지만 여기선 아니다. 

- 실제로 안 되는 이유: 
  맨 처음에 시작할 때 start commit이 어떻게 시작이 됐냐, 
  1) remote가 initial commit을 했다. 
  2) 그리고 A, B가 각각 clone을 받았다. 
      그럼 A, B가 각각 1을 받았다.
  3) 그러고 A가 index - push
  4) B가 about - push 하려던 중에 에러 
  ![image-20210621153422806](013-ing.assets/image-20210621153422806.png) 

   

  ![image-20210621153445787](013-ing.assets/image-20210621153445787.png) 

  ① initial clone 받을 때까진 3곳 모두 다 싱크가 맞는 거다.  

  그런데 여기서 A의 ②commit = index. 
  B의 ②commit = about

  즉, 근본이 다른 commit이다. 
  그런데 A가 먼저 push를 했다. 그러면 push를 했으니깐 remote의 ②도 A의 commit을 따르는 거다. 

  그러고 나서 B가 ②를 밀어 넣으려고 하니깐, 애초에 완전히 다른 커밋인데 그게 문제다. 그래서 안 된 거다. 

- commit - hash 번호만 봐도 알 수 있다 
  git log --one line으로 보면 알 수 있다. 
  ![image-20210621154623701](013-ing.assets/image-20210621154623701.png) 

  보면 첫번째 hash는 완전 같다. 

  그런데 2번째 hash는 완전 다르다. 

- 그래서 push 하니깐 뜨는 걸 보면 
  ![image-20210621155139806](013-ing.assets/image-20210621155139806.png)    

  노란 글씨 : 너 한 템포 늦었어.
  즉, 너가 push 하려고 했는데 이건 안 돼. 
  왜? A가 먼저 했으니깐 ②은 A가 먹어버린 거야.
  remote contains work that you do not have locally. 너 컴에 없는 work(커밋)이 있어. 

  너가 원하는 건 아는데, 미안하지만 일단 git pull 먼저 해, 저걸 먼저 받아와야 돼. 

  ![image-20210621161635619](013-ing.assets/image-20210621161635619.png)  

  (cf. 브랜치는 어떤 작업 중 마지막 작업을 가리키는 포인터 또는 *Refs*이다. / ref = 리포 / *Repo*란 필요시 여러가지 *Git* repository를 통합하여 Android 개발 workflow를 자동화합니다.)

- git pull origin master
  ![image-20210621161744697](013-ing.assets/image-20210621161744697.png)  

  머징 했더니 이런 문구가...!?!?? 머징머징...

- 당연하죠! 받아왔더니 about.html이 ....

  ![image-20210621161905040](013-ing.assets/image-20210621161905040.png)  

  index.html이 들어온 건 좋아~ 그런데 애초에 같은 영역이 아니라 다른 영역을 건든 거기 때문에 딱 합쳐졌어요. 

- 파이참 열기 귀찮을 때, cat 
  ![image-20210621162120604](013-ing.assets/image-20210621162120604.png)    

  readme.md를 빠르게 보는 건데 
  B꺼는 위에 있고, A꺼는 아래에 있고. 
  골라야 할 때가 왔어... 

  근데 해결방법은 똑같아.
  md 파일을 열어서 보자. 
  ![image-20210621162218696](013-ing.assets/image-20210621162218696.png)  

  여기서 [ ctrl + / ] 누르면 다른 거 보임. 
  실제 작성한 내용 / 보이는 내용 
  여기서 실제 작성된 내용 보면 

  ![image-20210621162340176](013-ing.assets/image-20210621162340176.png)  

  B는 둘 중 골라야 돼, 받아 버렸잖아. 해결은 똑같아. 상황은 바뀌어도 우리가 하는 일은 바뀐 게 없다. 그냥 고르면 돼. 

- 이렇게 변경 중에 A가 또 추가하고 push 하면 ③을 먹어보림. A는 아싸~ 잘 된다. 왜? A가 선점했기 때문에. 
  그런데 b는 다 고치고.. 그래 같이 일한 거니깐 README 손수 수정해서.. 이제 되겠지?! 
  다시 push하려고 하는데... 안 돼. A가 넣었으니깐. 그럼 또 pull .. 고치고. ... 무한 반복. 

- 이래서 master에 push 하면 안 된다. 
  왜? 이런 충돌
  그리고 대의적으로 
  팀이 결과물을 만드는데, 충돌이 생겼을 때 사람과 사람이 이야기를 해서 이게 맞는 거 같은데, 어 그러게 맞는 거 같다. 아니면 아예 이렇게 수정을 할까? 등의 합의의 과정이 있어야 하고 합의의 결과가 master commit이 되어야 하거든요.

  그런데 지금 보여준 구조는 합의를 B 혼자 하고 있는 모습. 이러다 B가 화나서 A 일 다 지워 버릴 수도 있다. 이것조차 합의 없이 결정을 하게 되는 거다. 

  그래서, 결정은 team에서 같이 해야 돼. team의 공간인 github에서 같이 해야 된다. 
  전화, 슬렉, 디스코드, 카톡으로 얘기할 수 있지만 그건 사람 대 사람의 의사소통이고 

  실제 결정 **땅땅땅**은 team의 github 이어야 한다. 

#### 7-8. 이래서 branch가 필요하다. 

- A 입장에선 git push origin master / git pull origin master 둘 다 문제 없음 

- B가 문제인데. 
  git status 했는데 빨간 글씨나 머징 뜨면 고치고 
  없다면 commit 후 push 
  ![image-20210621165132568](013-ing.assets/image-20210621165132568.png)  

- 즉, B가 해야 하는 건 어떻게 해서든지 이 3개의 싱크를 맞춰야 한다. 
  ![image-20210621165224253](013-ing.assets/image-20210621165224253.png)  

  난리난 그래프 체크 
  A가 index 생성, B가 about 생성
  B가 merging 하는 동안에 또 뭐 들어오고 날리남.

  일단, 다 멈춰. 작업하지 말고 다 멈춰. 
  그리고 통일해. 
  A-remote-B (3)이 다 싱크 맞을 때까지.

- 싱크 맞는지 확인하는 방법은? 
  ![image-20210621165526970](013-ing.assets/image-20210621165526970.png)  

  둘 다 해보고 / A도 마찬가지로.

  - git push origin master / 에러 

  ![image-20210621165619453](013-ing.assets/image-20210621165619453.png)  

  - git pull origin master
  - 그러고 나서 다시 
    git push origin master 

  이걸 계속 반복(A-B 둘 다) 하는 거야. 할 일 없다고 나올 때 까지. 

  ![image-20210621170008747](013-ing.assets/image-20210621170008747.png)  

  push - pull 4번 정도 하다보면 이렇게 나온다. 

  A, B 둘 다 
  "Everything up-to-date"
  "Already up to date" 나올 때까지 되면. 

  싱크가 맞는 거다. 이 상태에서 협업을 들어가는 방법을 다시 배워보자. 

  

#### 7-9. 현재 상태 : A - remote -B 싱크 동일 

![image-20210622021722883](013-ing.assets/image-20210622021722883.png)  

#### 7-10. git switch -c 

- 뒤에 붙는 이름이 branch name. 

- A: git switch -c feature/login
  	touch login.py

- B: git switch -c patch/index

- 각자 branch 준비 
  ![image-20210604171643623](013-ing.assets/image-20210604171643623-1624296286330.png) 
  지금 이 상태가 바로, remote에 A, B가 싱크를 맞춘 상태 + branch 준비

- A: README 작성 
  <img src="013-ing.assets/image-20210604171724401.png" alt="image-20210604171724401" style="zoom:65%;" />  

- 거기서 add를 하면 줄이 나오고

  거기서 commit을 하면 점이 찍힘 (A, B 각각)

  ![image-20210622022739892](013-ing.assets/image-20210622022739892.png)  

#### 7-11. 그리고 A에서 remote로 push 할 때 

git push origin feature/login
이렇게 자기 브랜치 이름으로 보냄 

![image-20210622023018964](013-ing.assets/image-20210622023018964.png)  

그러면 저렇게 main 외에도 feature/login이 branch로 보이게 됨. 그럼 A-remote 상태는 
![image-20210622023117276](013-ing.assets/image-20210622023117276.png)  

- B는 파일명을 바꾸고 싶음
  mv index.html index!.html
  vim index.html

  ​	 [i - blahblah - esc - :wq ] 이렇게 변경도 가능 
  ![image-20210622023434622](013-ing.assets/image-20210622023434622.png) ![image-20210622023447887](013-ing.assets/image-20210622023447887.png)  

  그러고 readme 수정
  start README.md
  add & commit

  ![image-20210622023552586](013-ing.assets/image-20210622023552586.png)  
  git push origin patch/index

#### 7-12. 발송 완료! 

그러면 그림은 이런 상태 !

![image-20210622023624016](013-ing.assets/image-20210622023624016.png) 

<img src="013-ing.assets/image-20210622023717771.png" alt="image-20210622023717771" style="zoom:67%;" />  



#### 7-13. merge in TEAM

여기서 마스터(main)가 제일 중요 함. 
병합은 main에서. 
그런데 3 점이 한번에 같이? nope. 

<img src="013-ing.assets/image-20210604172542170-1624297134825.png" alt="image-20210604172542170" style="zoom:67%;" />  이런 순서로. 자세히 봐보자. 


![image-20210622024039120](013-ing.assets/image-20210622024039120.png) 

각각에서 Compare & pull request가 뜸. 
깃헙에서만 pull request라고 부르고 보통 merge request 라고 부른다. 
여튼 이 초록 버튼은 A랑 B에서 team에게 merge 해달라는 요청을 보낸 거다. 
![image-20210604172806119](013-ing.assets/image-20210604172806119-1624297411307.png)  

- 거기서 초록 버튼을 누르면 
  ![image-20210604172842284](013-ing.assets/image-20210604172842284-1624297434793.png)  

  feature/login >> master 로 보내도록 나옴. 
  그러면 그 옆에 
  ![image-20210604172856540](013-ing.assets/image-20210604172856540-1624297502386.png)  라고 뜬다. = "어, 그거 가능해"

- 그러면
  ![image-20210604172912783](013-ing.assets/image-20210604172912783-1624297568135.png)  

  1)  Write 부분에 쓰자. 
  	"나는 A야, 지금 로그인 관련 1차 기능 완성"

  ​	"#로그인 관련1차 완성 
  ​	-회원 DB 생성
  ​	-cookie 설정 완료" 

  

  2) 한 명 지정해서 review & Assign 요청 가능 

  ​	<img src="013-ing.assets/image-20210604173032201-1624297783062.png" alt="image-20210604173032201" style="zoom:67%;" />  

  ​	<img src="013-ing.assets/image-20210604173050633-1624297815893.png" alt="image-20210604173050633" style="zoom:67%;" />  

  

  3) Create pull request 누름. 
  	이거 누르면 합쳐지나? nope. 
  	그냥 말풍선 올린 거 

  4) 그러면 어떤 상황 ? 

  ​		![image-20210622025224793](013-ing.assets/image-20210622025224793.png)   

  - 여기서 Merge pull request 누르면 합쳐짐. 
    내가 해도 되고, 다른 사람이 해도 됨. 
    정말 사회생활을 축소해 놨다. 

  - 그리고 그 아래에 Write에 다른 사람이 피드백 올릴 수 있다. 

  - 근데 여기서 이건 받을 수 없다고 표현할 수도 있어야 겠지? 
    Close pull request
    ![image-20210622025604916](013-ing.assets/image-20210622025604916.png)  

  - 그 결정을 내리는 과정은 안에 내용 체크, 이모티콘도 달고, 수정도 달 수 있음
    ![image-20210622025738607](013-ing.assets/image-20210622025738607.png) 

  - 그러고 결론적으로 결정을 내리면 
    아까 Merge pull request 누르고 
    Confirm merge 누르면 완성! 

  - 이렇게 merged로 바뀌고, 
    ![image-20210622025908099](013-ing.assets/image-20210622025908099.png) 

    

    master에 병합된 내용을 볼 수 있다. 

    ![image-20210622025936214](013-ing.assets/image-20210622025936214.png)  

    

  - 현재 이 상태를 그림으로 그리면 
    ![image-20210622030121879](013-ing.assets/image-20210622030121879.png) 

    

  - B도 이걸 반복하면 
    ![image-20210622030158966](013-ing.assets/image-20210622030158966.png)  

    이렇게 바뀜. 

  

#### 7-14. 그 후 A, B

- 그런데 중요한 건, 현재 A, B의 상태는 ?
  ![image-20210622030239190](013-ing.assets/image-20210622030239190.png)  

  ​	![image-20210604173959357](013-ing.assets/image-20210604173959357-1624298591705.png)  

  

  ![image-20210622030332619](013-ing.assets/image-20210622030332619.png) 

  

  **55e6 - [ f205 or 3806 ]**

  ![image-20210604174106750](013-ing.assets/image-20210604174106750.png)  

  (참고로, 저 아래 더러운 그래프 그림은 아까꺼)

#### 7-15. 여기서 할 건 ? pull 과정

- A, B 각각 먼저 master로 이동 
  ![image-20210604174219417](013-ing.assets/image-20210604174219417.png)  

  master에서 master를 받는 게 핵심. (master가 최신인 상태니깐)

- 그러고 log로 상태 보면 
  ![image-20210604174256669](013-ing.assets/image-20210604174256669-1624298959664.png)  
  A, B 둘 다 똑같이 이 상태로 있어야 함.



#### 7-16. 그러고 branch 삭제 & 생성

![image-20210622031017448](013-ing.assets/image-20210622031017448.png)  

- 그 후에 각자 다시 다른 작업을 시작한다. 
  ![image-20210604174357001](013-ing.assets/image-20210604174357001-1624299042556.png)  



#### 7-17. 두 개가 충돌할 경우는 깃허브에서 같이 수정

![image-20210604174815999](013-ing.assets/image-20210604174815999-1624299352257.png)  

![image-20210604174840276](013-ing.assets/image-20210604174840276-1624299366325.png)  





git_TEAMwork.md

```
git remote add origin https://github.com/KDT-study/Statistics.git
git remote -v
git remote remove origin
git pull origin master
git rm --cached + file.name
git pull origin master
git branch Yoojung
git branch
git checkout Yoojung
git add . && git commit -m '이산형 확률변수, 발표자 한유정'
git push origin Yoojung
git reset HEAD^
```



 



### cf. 

#### 1. setting

![image-20210607040732872](013.assets/image-20210607040732872.png)



#### 2. 추천교재 

![image-20210618123808149](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618123808149.png) 



#### 3. 타이포라 이미지 설정 

![image-20210618145656929](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618145656929.png) 

#### 4. checkout vs switch

![image-20210618151902552](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618151902552.png) ![image-20210618154233883](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618154233883.png) 



#### 5. 깃허브 - 시크릿 모드 

![image-20210618155709344](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210618155709344.png)



#### 6. $ git merge --help

: 인터넷 창 열리면서 어떻게 도움을 받을 수 있는지 안내창이 나온다. 



#### 7. git 배우는 홈페이지

https://backlog.com/git-tutorial/kr/
쉽게 배울 수 있는 교재 느낌 

#### 8. ctrl + c : 취소  

#### 9. git config

git config user.name
git config user.email

이메일 수정할 때 
git congig : 서명이라 안맞춰도 돼
그런데 email은 맞춰야 함. ![image-20210604144943933](013-ing.assets/image-20210604144943933-1624300276097.png)  

- 내 이메일 확인하는 방법

  git config --global user.email
  ![image-20210604145157736](013-ing.assets/image-20210604145157736-1624300378955.png)  

  or 
  git remote -v

- 아무것도 안나오면 
  git remote add origin <url>



#### 10. neo@hphk.kr

유태영 강사님 이메일 주소

#### 11. git 명령어

```
git add .
git commit -m ''
git add . && git commit -m ''
git status 	
	stage에 올라간 걸 내리고 싶다면 restore 하면 돼 라고 명령어 보여줄 거다 
	git restore / 따라치기만 하면 돼. 
.gitignore

git switch master
git merge dev
git branch -d dev
git switch -c my-branch
git log
git log --oneline
git log --oneline --decorate --graph

git commit --amend   [ i ] - [ esc ] - [ :wq ]

git merge <>     : master 자리에서, 먹을 애를 적음
git merge --help

ctrl + c : 취소 

git config --global core.editor "vim"
cf. 기본 에디터(git commit 했을 때 뜨는 에디터)를 vim으로 바꾸는 명령어

git push origin master 
하면 커밋에 추가된 내용만 올라가는 거다. 
파일이 그냥 올라가는 게 아님 
```

![image-20210622033730725](013-ing.assets/image-20210622033730725.png) 

마지막에 to~뭐라고 뜨면 성공한 거.커밋명이 다 다른네. 각 각자 마지막 영향 받은 커밋 받고
test도 올라간 거 확인 가능 

맨날 커밋하고 푸쉬? 푸쉬는 그냥 하루 한 번에 가능
커밋은 그 때그때 , 의미 있게
<img src="013-ing.assets/image-20210622033857494.png" alt="image-20210622033857494" style="zoom:67%;" />   

![image-20210622034000358](013-ing.assets/image-20210622034000358.png) 



#### 12. talk

유태영 강사님 현실언어 사용해줘서 친근한 수업 너무 재밌었습니다 XD  삽질 총량 법칙 화이팅!!

어려워서 버겁기도 했는데 재밌게 집중해서 잘 배웠습니다! 삽질 총량 법칙을 기억하면서 제가 되어 가겠습니다 XD 감사합니다..!!! 



sw 중심 / 기술 꾸준 관심 테크 적용 깃헙 관리 포트폴리오 

삽질 총량의 법칙 = 내가 된다. 
멀리서 보면 상관 없다
삽질 시간이 필요. 
깃도 일조 할 것이다.

나는 전설이 된다. 



#### 13. remote 이름 바꾸기 

git remote -v 해서 이름 상태 보고 
거기서 
git remote -h 여기서 h가 보통 help예요. 하니깐 
rename 같은 걸 찾아보자. 

git remote rename <old> <new>


#### 14. git push -u  ???

#git push -u TLI main  / -u 안 배움 배운 거 찾아보자 



