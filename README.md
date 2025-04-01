# mongoose-usage
mongoose의 다양한 연산자와, 프레임워크 사용법을 예제와 함께 정리한 리포지토리

</br>
</br>

# Before Read

mongoose는 데이터를 조회할 때 일반 필터링과 파이프라인 방식으로 나뉩니다.

</br>

# Normal-Filtering

Normal-Filtering은 데이터를 조회할 때, query단계와 projection 단계로 나뉩니다.

- query : 조건에 맞는 문서를 반환하는 단계
- projection : 해당 문서에서 반환할 필드를 지정하는 단계

구문: db.collection.find(query, projection)

</br>

# PipeLine

Aggregation Framework를 활용하여 여러 단계에 걸쳐 데이터를 처리하고 변환하는 방법

- aggregate([])의 배열에 Stage라는 변환 작업들을 나열하여 보다 정교하게 필터링, 변환할 수 있게 합니다.
