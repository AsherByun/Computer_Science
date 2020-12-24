# Statement & Prepare-statement
*** PreparedStatement 와 Statement의 가장 큰 차이점은 캐시(cache) 사용여부이다.**

1) 쿼리 문장 분석

2) 컴파일

3) 실행

Statement를 사용하면 매번 쿼리를 수행할 때마다 1) ~ 3) 단계를 거치게 되고, PreparedStatement는 처음 한 번만 세 단계를 거친 후 캐시에 담아 재사용을 한다는 것이다. 
만약 **동일한 쿼리를 반복적으로 수행**한다면 PreparedStatment가 DB에 훨씬 적은 부하를 주며, 성능도 좋다.
