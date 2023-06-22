### 로라(LoRA, Low-Rank Adaptation) 
 - 대용량 데이터와 대규모 파라미터로 학습될 모델들(Large-Scale Pretrained Model)
 - GPT3 이후, 라지 스케일 Language Model 수 없이 등장 (7billion)
 - 엄청난 큰 기업들만이 이러한 모델을 학습시킬수 있었다. 그러다 보니 한계가 있었다. 
 - Over-Parametrized Model이다. 
	- 예를 들어 영어논문을 잘 요약하는 모델을 만들고 싶다면, 논문을 학습시켜야 하는데 너무 방대한 데이터. 
	- 따라서 구글/메타가 만든 모델을 갖고 사용하면 된다. 그런데 이미 10억개 데이터로 학습된 모델로 훨씬 작은 데이터를 작업한다. 
	- 이런 작업을 downstream task라고 부름. 여기에는 엄청난 하드웨어 리소스가 필요하다. 개인단위에서는 불가능.
	- 이러한 리소스 제한은 너무 많은 parameter때문에 발생. 작은 데이터의 결과값은 그렇게 많은 학습데이터가 필요하지 않은데, 작은 데이터에서의 결과 추출도 너무 큰 모델 속에서 작업되기 떄문에 하드웨어 리소스 과도하게 많게 됨 (Over-Parametrized Model)
	- 따라서, 거대 모델 중에서 필요한 정보를 찾아서 그것만 갖고 결과를 추출하는 방식으로 학습 데이터를 "Low-Rank space"로 변환하는 아이디어가 등장함. "Low Rank"는 주어진 데이터가 담긴 행렬의 위치 중에서 가장 핵심적인 정보만 뽑아쓰겠다는 의미. 

* LoRA(Low-Rank Adaptation)
 - 컨셉 : 이미 학습된 정보만 가져올거야. 그런데 옆에 중요한 정보만 뽑아오는 친구가 도와줄거야. 
 - 수학적인 부분은 너무 어려워서 패스 ㅠ (두 개의 매트릭스를 곱하면, 아 이거 분명 배웠는데...) 
 - 12,888차원에서 1~2차원만으로 Pre-trained weight를 optimize. 
   
* LLM에서 LoRA의 목표
 - 거대 모델에 들어가는 작은 입력에 효율적으로 자원을 활용하기 위한 언어모델
 - No Additional Inference Latency

* Applying LoRA to Transformer
 - 21년에는 LLM BASE MODEL인 Transformer에 적용. 
 - Lora는 실제 LLM Tuner로 제격이다. 1.2TB -> 350GB로 줄이는 등...
 - r = 4로 두면 350GB가 35MB가 된다.

* 이해가 안되는게 많네요. 미래의 내가 이해해주길 바라며, 머신러닝 복습 들어갑니다!!
* 강사님이 코드 공유해주셨는데, 혹시 저희 스터디에 공유가 가능하면 같이 보면서 돌려보는 것도 재미있을것 같네요! 필기는 여기까지!