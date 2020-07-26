# Pickle 
- 파이썬 객체를 바이너리 파일로 저장 및 읽어오기 위한 프로토콜
- 멀티프로세싱 개발시 서로 다른 프로세스 간의 데이터 전달을 위해 사용할 수 있다. 
- 한편, Pickle은 모든 타입의 객체에 대해 지원되지는 않는다. 지원되지 않는 객체에 대해 시도할 경우 에러가 발생된다. 특히 파이썬 외부 패키지가 제공하는 객체의 경우 내부 구조 파악 없이 사용하면 위험.
  - 참고 : https://docs.python.org/ko/3/library/pickle.html#what-can-be-pickled-and-unpickled


# Marshmallow
- 객체를 파이썬 기본 데이터 타입으로 변환 (serialization)시킬 때 쓰는 라이브러리 
- https://marshmallow.readthedocs.io/en/stable/index.html
- load_only : serialization에서 제외할 항목 설정. 즉 아래와 같이 코드를 작성하는 경우 serialization시 id와 b 값만 반환됨. API 결과로 1) 노출되서는 안되는 경우, 2) 사용되지 않는데 불필요하게 데이터 양이 늘어나 속도 이슈가 생기는 경우 사용할 수 있음. 
```python
class AModel(db.Model):
  ...
  id = db.Column(db.Integer, primary_key=True)
  a = db.Column(db.String(100))
  b = db.Column(db.String(100))

class AModelSchema(ModelSchema):
    class Meta:
        model = AModel
        load_only = ("a")
```