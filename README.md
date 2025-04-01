# mongoose-usage
mongoose의 다양한 연산자와, 프레임워크 사용법을 예제와 함께 정리한 리포지토리

</br>
</br>

# Before Read

mongoose의 연산자는 문서를 여러 형식으로 검색할 수 있고, 여러 형태로 가공하여 반환할 수 있습니다. 이 리포지토리에서는 단일 문서 반환을 다루기 보다 find(), aggregate()와 같이 여러 문서들을 담은 배열을 반환하는 메서들 내에서 데이터의 쿼리, 가공 등에 자주 쓰이는 연산자들을 정리합니다.

</br>

# find()

find 메서드는 조건에 맞는 문서들을 조회할 때 필요한 query를 필수적으로 받고, 해당 query로 조회된 문서들을 가공하는 projection을 선택적으로 받습니다.

ex) await User.find({ score: { $elemMatch: { $gte: 80 } } }, { name: 1, age: 0, score: 1 });
- 위 예제에서 { score: { $elemMatch: { $gte: 80 } } }가 query이고, { name: 1, age: 0, score: 1 }가 projection 입니다.

query는 기본적으로 조건에 맞는 문서들을 찾아 원본 그대로 반환합니다. projection은 필요한 필드만 유지시키거나 새로운 필드를 추가하는 등 결과물을 가공하는 기능을 합니다.

</br>

# aggregate()

aggregate는 여러개의 Stage를 순차적으로 거치는 pipeLine을 구축할 수 있습니다. 각 stage 특정 연산을 수행하며, 결과를 다음 Stage로 전달하여 보다 복잡하고 정밀한 가공이 가능합니다.

ex) await User.aggregate([ { $match: { age: { $gte: 30 } } }, { $projection: { name: 1, age: 0, score: 1 } } ])

- aggregate은 Stage라는 작업들을 포함하고있는 배열을 인자로 받습니다. 이 Stage 작업들을 수행하는 과정을 pipeLine 이라고 합니다.

