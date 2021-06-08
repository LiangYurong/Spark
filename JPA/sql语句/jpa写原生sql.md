

1.原生sql语句，在dao层写
2.不需要写public，因为是interface
3.写原生sql，需要写上nativeQuery = true

```txt
@Repository
public interface SurveyDao extends JpaRepository<Survey,String> {
    @Query(value = "select * from t_survey where survey_state = ?1",nativeQuery = true)
    List<Survey> findBySurveyState(String surveyState);
}
```
