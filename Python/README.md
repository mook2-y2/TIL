# Pickle 
- 파이썬 객체를 바이너리 파일로 저장 및 읽어오기 위한 프로토콜
- 멀티프로세싱 개발시 서로 다른 프로세스 간의 데이터 전달을 위해 사용할 수 있다. 
- 한편, Pickle은 모든 타입의 객체에 대해 지원되지는 않는다. 지원되지 않는 객체에 대해 시도할 경우 에러가 발생된다. 특히 파이썬 외부 패키지가 제공하는 객체의 경우 내부 구조 파악 없이 사용하면 위험.
  - 참고 : https://docs.python.org/ko/3/library/pickle.html#what-can-be-pickled-and-unpickled