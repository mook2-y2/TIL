# Inner Join, Outer Join 
- 조인(Join)이란 2개 이상 테이블을 서로 엮어 조회하는 것이다.
- Inner Join은 서로 매칭되는 것만 엮어 조회한다. 즉, 연결되는 테이블이 없는 경우 조회되지 않는다. Outer Join은 매칭 뿐만 아니라 미매칭 데이터도 함께 모두 조회한다.
- 예를 들어, A테이블을 정렬하기 위해 A테이블과 연결된 B테이블의 필드를 이용해야 하는데, A테이블 중 일부만 B테이블과 연결되는 경우 outer join을 사용해야 A테이블의 모든 결과에 대한 정렬 값을 얻을 수 있다. 
## Flask, Sqlalchemy 예시 
```python
# model.py
class ATable(db.Model):
    ...
    b_table = db.relationship('Btable')


class BTable(BaseModel, db.Model):
    ...
    field_to_order = db.Column(db.Integer)


# app.py
result = ATable.query \
            .join(BTable, isouter=True) \
            .order_by(BTable.field) \
            .all()
```
- 참고 : https://docs.sqlalchemy.org/en/13/orm/query.html#sqlalchemy.orm.query.Query.join.params.isouter

# NULLS FIRST, NULLS LAST
- ORDER BY 구문으로 정렬할때 NULL값을 앞쪽에 오게 할지, 마지막에 오게 할지에 대한 구문
- 위 Outer Join과 연결지어 A테이블 중 B테이블과 연결관계가 없는 (null) 것을 정렬시 상위로 올지 하위로 오게 할지 정할 수 있다. 
## Flask, Sqlalchemy 예시 
```python
# app.py
from sqlalchemy import desc, nullsfirst, nullslast

result = ATable.query \
            .join(BTable, isouter=True) \
            .order_by(
                desc(BTable.field).nullslast, 
                desc(Atable.created_at)) \
            .all()

```
- 참고 : https://docs.sqlalchemy.org/en/13/core/sqlelement.html#sqlalchemy.sql.expression.nullsfirst