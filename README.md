# Window length 및 Stride에 따른 예측 결과 성능 비교

## 1. Previous
### 지난 미팅에서 Window size (stride)를 각각 50 (10), 75 (15), 125 (25), 150 (30), 200 (40)으로 진행한 결과를 보여드렸습니다. 이에 model input으로 R2 저항을 포함시키지 않았을 경우와 포함시켰을 경우의 RMSE와 R2를 통한 성능을 살펴보았습니다. 결과적으로 window size가 줄어들 경우 RMSE값은 감소하는 경향이 있었으며 R2 값은 큰 변화가 있지는 않았음을 확인하였습니다. 길이가 길어질수록 학습 데이터의 수가 적어지기 때문에 성능이 안좋아진다고 예상할 수 있었으며 이에 추가적으로 극단적으로 window의 size를 줄인 결과도 살펴보고자 하였습니다. 해당 결과를 현 README 하단에 함께 업로드하였습니다. 

![RMSE ws result 1](https://github.com/sooyeon99419/example/assets/134259835/7488dfb3-487d-4c8f-873f-3c9048014f37)
![R2 ws result 1](https://github.com/sooyeon99419/example/assets/134259835/f9bc4b3b-f032-4ade-8296-d1f94e926f9b)

## 2. Result
### Window의 사이즈를 극단적으로 줄이기 위해 Window size (stride0를 각각 1 (1), 10 (2), 20 (4) 로 총 세 가지 경우에 대한 결과를 살펴보았습니다. 이에 예측 성능 비교 결과는 아래 그림과 같이 나왔음을 확인하였습니다.

![RMSE ws result 2](https://github.com/sooyeon99419/example/assets/134259835/3c8d300f-9913-4dba-9b8d-6d89cfe4ad04)
![R2 ws result 2](https://github.com/sooyeon99419/example/assets/134259835/bbdb3e9d-67c7-4e55-8ec8-fdb3eb279a8e)

### Window size가 극단적으로 줄어들었을 경우 성능은 매우 안좋게 나왔습니다. 이에 한 가지 이유로는 현재 사용한 데이터는 초당 12개의 데이터를 받고 있으며 current input control이 최소 1초동안으로 이루어지기 때문에 10개의 데이터로의 force 예측이 힘들었을 가능성이 있습니다. 또한 시간 term과 상관이 있기 때문에 성능 저하가 있었을 가능성도 있습니다. 현재 결과로는 20과 50에서의 성능 차이가 크게 나지 않는 것으로 확인되며 이에 window length가 20과 50 사이일 때 결과가 어떻게 나오는지 확인해보기 위해 두 가지의 경우를 추가하여 진행해보았습니다.

## 3. Final Result
### Window size를 30 (6), 40 (8) 총 두 가지 더 추가하여 결과를 살펴보면, 아래 그래프와 같이 20과 50의 경우와 거의 비슷한 결과를 보임을 확인하였습니다. 이에 데이터에 맞는 최적의 window length 및 stride의 길이를 알아볼 수 있었습니다. 이에 이전의 공기 중 취득 데이터 뿐만 아니라 물에서의 다양한 환경 변화 속에서의 데이터를 사용하여 머신러닝을 진행한다면 이에 맞는 최적의 window length를 찾아나가야 할 것으로 예상합니다.

![RMSE ws result 3](https://github.com/sooyeon99419/example/assets/134259835/9d2675cc-584c-46b0-a8f7-9134a33e0957)
![R2 ws result 3](https://github.com/sooyeon99419/example/assets/134259835/ebabc406-f644-4c6b-8602-7003135853b2)


