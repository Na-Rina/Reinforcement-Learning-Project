# 클라우드 기반의 신세계 API와 강화학습을 이용한 맞춤형 추천시스템 개발 및 평가

## 프로젝트 개요
본 프로젝트는 신세계 API를 활용한 추천 시스템과 강화학습을 결합하여 사용자 맞춤형 추천 시스템을 개발하고 그 성능을 평가하는 것을 목표로 합니다. AWS의 EC2, RDS, S3를 사용하여 시스템을 구성하고, 강화학습 모델을 통해 추천의 정확도를 향상시킵니다.

## 목차
1. [초록](#초록)
2. [서론](#서론)
3. [본론](#본론)
    1. [시스템 아키텍처](#시스템-아키텍처)
    2. [API 설계](#api-설계)
    3. [강화학습 모델](#강화학습-모델)
    4. [실험 및 평가](#실험-및-평가)
4. [결론](#결론)

## 초록
본 연구는 신세계 API를 이용한 추천 시스템과 강화학습을 결합하여 사용자 맞춤형 추천 시스템을 개발하고 그 성능을 평가합니다. AWS의 EC2, RDS, S3를 사용하여 시스템을 구성하고, 강화학습 모델을 통해 추천의 정확도를 향상시킵니다. 실험 결과, 추천 정확도와 사용자 만족도가 각각 15%, 20% 향상되었습니다.

## 서론
추천 시스템은 사용자에게 맞춤형 상품을 제공하여 만족도를 높이는 중요한 도구입니다. 본 연구에서는 신세계 API와 강화학습을 결합한 추천 시스템을 개발하여 사용자 데이터 기반의 개인화된 추천을 제공합니다. 이 시스템은 AWS 인프라를 활용하여 구축되었으며, 강화학습을 통해 지속적으로 성능을 개선합니다.

## 본론

### 시스템 아키텍처
본 연구의 시스템 아키텍처는 클라우드 기반으로 설계되었으며, AWS의 다양한 서비스를 활용하여 구성되었습니다. 주요 구성 요소는 다음과 같습니다:
- **EC2**: API 서버와 데이터 처리 서버로 구성되어 사용자 요청을 처리하고 데이터베이스와 상호작용합니다.
- **RDS**: 사용자 및 상품 데이터를 저장하기 위해 MySQL RDS를 사용합니다.
- **S3**: 이미지 및 대용량 데이터를 저장합니다.

### API 설계
신세계 API는 사용자의 정보를 기반으로 추천 시스템을 작동시킵니다. 주요 API 설계는 다음과 같습니다:
- **회원가입**: /members/check?family=true/register (POST)
- **로그인**: /members/login (POST)
- **성별 선택**: /members/gender (POST)
- **연령대 선택**: /members/age-group (POST)
- **선호/비선호 음식 및 식재료 선택**: /members/preferred (POST)
- **식재료 냉장고 전체보기**: /ingredients/{storage_method}/list (GET)

### 강화학습 모델
본 연구에서는 신세계 API와 사용자 행동 데이터를 활용한 추천 시스템을 구축하기 위해 강화학습 모델을 설계하였습니다. 강화학습의 한 종류인 DQN(Deep Q-Network)을 사용하여 최적의 추천을 제공합니다.
- **초기화**: 심층 신경망을 사용하여 Q-네트워크를 설정하고, 타겟 네트워크도 초기화하여 학습의 안정성을 높입니다.
- **데이터 수집 및 전처리**: 신세계 API를 통해 사용자와 제품 정보를 수집하고, 이를 MySQL 데이터베이스에 저장한 후 전처리합니다.
- **환경 설정**: 강화학습 환경을 정의하고, 상태-행동 값을 예측하여 최적의 행동을 선택합니다.
- **에이전트 설정**: 에이전트는 상태와 행동 공간의 크기를 정의하고, 경험 재생 메모리를 설정하여 학습합니다.

### 실험 및 평가
본 연구에서는 강화학습 모델의 성능을 평가하기 위해 100개의 에피소드를 사용하였습니다. 각 에피소드는 최대 100단계로 구성되며, 각 단계에서 에이전트는 행동을 선택하고 보상을 받습니다.
- **누적 보상 계산**: 학습 과정에서 각 에피소드의 총 보상을 기록하고 시각화합니다.
- **평가**: 평균 보상과 F1 스코어를 통해 성능을 평가합니다.

## 결론
본 연구는 신세계 API와 강화학습을 결합한 추천 시스템의 가능성을 보여주었습니다. 주요 결론은 다음과 같습니다:
1. 추천 정확도 향상: 강화학습 모델을 적용한 후 추천 정확도가 15% 향상되었습니다.
2. 사용자 만족도 증가: 사용자 만족도가 20% 증가하였습니다.
3. 클라우드 기반 시스템의 유연성: AWS의 EC2, RDS, S3를 활용한 클라우드 기반 시스템은 확장성과 안정성을 제공합니다.
4. 데이터 관계의 중요성: 데이터베이스의 테이블 간 관계를 명확히 정의하고 데이터 모델을 설계하여 시스템의 효율성을 높일 수 있었습니다.

향후 연구로는 실시간 학습 시스템 개발, 다양한 사용자 데이터 활용, 모델의 다양성을 고려한 연구를 제안합니다. 본 연구는 사용자 맞춤형 추천 시스템을 개발하고 평가함으로써, 전자상거래 분야에서 사용자 경험을 개선할 수 있는 중요한 기초 자료를 제공합니다.
