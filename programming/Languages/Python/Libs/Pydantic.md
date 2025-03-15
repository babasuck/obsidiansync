Data validation библиотека, использует под капотом механизм [[Type hints]].
Суть библиотеки в том, что можно создавать модели по примеру датаклассов, но с валидацией, перед тем как создать объект такой модели, Pydantic проверит, что все поля соответствуют типу, можно добавить свои валидации.
## Создание модели

```python
from pydantic import BaseModel

class User(BaseModel):
    id: int  
    name: str = 'John Doe'  
    signup_ts: datetime | None  
    tastes: dict[str, PositiveInt]
```

Здесь:
`id` - обязательное поле с типом `int`
`name` - необязательное поле с типом `str`, со значением по умолчанию
`signup_ts` - обязательное поле либо `datetime` либо `None`
`tastes` - обязательный словарь с ключами строками и значениями `Annotated[int, Gt(0)]`
