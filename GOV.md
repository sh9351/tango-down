# gov.kr
야야 잘들어봐, 내가 정부24 턴 썰 들려줄까? 사실 이건 좀 예전 이야기긴 한데, 사건의 시작은 이래.
난 그냥 평범하게 사이트 돌아다니고 있었다. 진짜로. 그러다 정부24라는 사이트를 발견하게 되었어. *<sh9351은 야생의 정부24를 발견했다!>* 암튼 그래서 나는 갑자기 생각이 들었어.
*이거 사용자 인증용으로 사용할 수 있겠는데?* 사실 나는 인증에 대하여 정말 악감정을 가지고 있어. 아니 진짜, 웹서비스 하나 하려고 하는데 법으로 사용자 인증을 강제해.
그러면 인증을 어케 하냐? 그것도 법으로 인증된 인증 수단만 가능해. 근데 그건 뭐다? 다 돈이다. Money. 휴대폰 인증만 봐도 건당 돈 받는게 정상이냐? 이거는 진짜 정부가 법 만들고
이통사들이 꿀 빠는 거 아니냐? 암튼 그래서 나는 이러한 *정부24를 이용한 무료 사용자 인증*에 감탄했지. 그래서 바로 코드 짜러 고! 나는 특히 코드를 짜기 가장 쉬울 것 같은 지문인증을 택했어.
그거때문에 손 씻느라 고생 좀 하긴 했지만, 그래도 어찌저찌 완성. QR코드 생성 후, 사용자가 인증을 했다고 하면, 정부24에 확인을 하는 거지. 그 후에는 링크를 누르면 그 정부24 계정으로 로그인
할 수 있는 주소까지 넣게 되었어. 근데 여기서 내가 조금 헷갈린 것이 있었거든? 그래서 그 주소에 들어가는 사용자 ID가 undefined가 된거야. 이러한 오류 개발하다 보면 자주 있잖아.
그냥 변수명 잘못 쳤다고 해서. 암튼 난 그래서 아무것도 모르고 그 링크를 클릭 했거든? 근데 갑자기 정부24 화면에 나의 이름이 아닌 다른 사람의 이름이 뜬거야. ?? 뭐냐? 해서 난 다시 한번
코드를 실행해서 로그인을 했어. 야 근데 있잖아, 원래 아무것도 바꾸지 않은 코드는 다른 결과를 기대하면 안되잖아. 방금 보았던 그 사람의 이름이 또 뜨는 거야. 이번에는 무언가 진짜 잘못된
것을 직감하고 한번 My 탭에 들어가 보았어. 근데 이게 뭐야? 이 생판 모르는 남의 개인정보가 다 나와 있잖아? 쩝... 그래서 나는 이걸 정부24의 버그로 알로 곧장 "그" 디스코드 서버에 올렸지.
아직도 그 채팅 남아 있어, 검색 해보면. 암튼 난 그래서 그냥 일시적인 정부24 오류로 생각하고 있었지. 아 근데 보니까, 그 로그인 주소의 아이디를 혹시 다른 걸로 하면 어떻게 되나 싶었어.
그래서 한번 우리 아빠꺼 아이디로 해봤다? 잘됨. 엄마꺼? 잘됨. 그와중에 우리 엄마가 최근에 무슨 서류 떼셨던거까지 다 나와. 헐. 그래서 이 취약점을 간단하지만 조금은 복잡하게 정리하자면 이래.

**정부24는 이사람이 지문인증을 완료했는지, 아니면 이 아이디가 맞는지, 심지어 Transaction ID가 있는지(!) 까지도 확인을 안해.**

**한마디로 요약하자면 : "너가 애야? 오늘부터 그래라"**

뭐 이건 진짜 너무한거 아니냐고. 진짜로. 어떻게 잼민이도 안하는 결정을 내려서 잼민이에게 털리냐. 이거는 단 코드 한줄의 문제가 아니라, 정부24의 개발자들이 직접 내린 결정이야.
모든 체크를 다 스킵하고 무조건 인증 토큰을 발급해주는 거지. 무조건. 말 그대로 *아이디만 있으면 로그인이 되는* 상황이였어. 근데 더 가관인건 뭔지 알아? 이 후의 일이야.
내가 이거를 발견한 순간 온갖 난리를 떨었지. 국정원에도 제보하고, 국정원에도 전화하고, 정부24에도 전화하고, 정부24에도 1 : 1 문의하고, 정부24가 전화하라는 데로 전화하고,
정부24가 전화하라는 데로 전화를 하니 거기서는 다시 원래 번호로 전화하라고 하고. 내가 왜 이렇게 호들갑을 떤줄 알아? 왜냐하면 **나의 개인정보가 유출될 수 있기 때문이야.**
솔직히 요즘에는 비밀번호 관리 다 잘하지. 사이트마다 비밀번호 다르게도 하고.~~(물론 나는 안하지만)~~ 근데 도데체 어떤 사람이 사이트마다 아이디를 다르게 하냐? 아니 애초에, 다른 사람의
아이디를 아는 과정이 얼마나 어려운가? 지금 디스코드에서 아무 프로필이나 클릭해도 연동된 ID가 널려있는데, 여기에서 사이트마다 ID를 다르게 하는 사람이 몇이나 될까? 암튼 그래서 난 처음에는
내심 기대했었어. 아 이 취약점 자세한 내용은 공개도 안하고 제보도 잘 해주었으니 한 ***절대시계 정도는 받지 않을까?***


나도 이러한 :DOG:소리를 하던 내가 후회된다. 절대시계는 커녕 고맙다는 말 한마디도 듣지 못했다. 암튼 그래서 하도 오두방정을 떠니 문자 하나 왔어. 전화 주라고.
그래서 전화했더니, 걍 취약점 고쳐졌다고 하고 어케 이 취약점 발견했냐고 묻고 끊더라. 그래서 결국에는 그들이 말한 "대처"가 뭔질 알아?
![image](https://user-images.githubusercontent.com/70079686/183073155-3f56259f-bd43-445b-80ae-dae2f70c494d.png)

근데 더 가관인건 뭔지 알아? 내가 이 취약점을 처음 발견한 것이 무려 **5월**이라는 거야. 그러니 지금 시간으로 **3개월**동안 이렇게 서비스를 막아둔 거야.
![image](https://user-images.githubusercontent.com/70079686/183073507-38a89ca6-c321-40c3-ba9b-9e38aef67255.png)


~~그래서 오늘의 결론은? 내 세금 돌려줘~~

## Tango down - gov.kr - 개인
