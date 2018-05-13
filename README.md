

```python
import os
import csv
import pandas as pd
```


```python
# Set path for file
file01= "schools_complete.csv"
file02="students_complete.csv"

```


```python
schools=pd.read_csv(file01, encoding="utf-8")
students=pd.read_csv(file02, encoding="utf-8")

```

 <font color='green'>Explore the data </font>


```python
schools
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
  </tbody>
</table>
</div>




```python
students.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>



 <font color='green'>Rename some columns</font>


```python
renamed_schools = schools.rename(columns={"name":"school name"})
renamed_students = students.rename(columns={"name":"student name", "school":"school name"})
renamed_schools.head()
renamed_students.head()
merged= pd.merge(renamed_schools, renamed_students, on="school name")
merged.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Student ID</th>
      <th>student name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>



 <font color='green'>Merge the two data frames and generate the District summary</font>


```python
merged_district=merged.loc[merged["type"] == "District", :]
merged_district.head()

# Total budget
merged_district["Total_budget"] = merged_district["budget"].unique().sum()
total_budget=merged_district["budget"].unique().sum()

# Total number of schools 
merged_district["Total_number_of_schools"] = len(merged_district["school name"].unique())

# Total number of students
merged_district["Total_number_of_students"]= len(merged_district["student name"])
total_students=len(merged_district["student name"])

#budget per student
merged_district["budget per student"] = total_budget / total_students

# average math and reading score
merged_district["average_math_score"] =merged_district["math_score"].mean()
merged_district["average_reading_score"] =merged_district["reading_score"].mean()
merged_district=merged_district.drop(columns=["gender", "grade","School ID","Student ID"])
merged_district.head()

# percent of passing math
number_of_math_passing_student= merged_district[merged_district["math_score"] > 70].count()["school name"]
number_of_math_passing_student
merged_district["math_passing_%"]= (number_of_math_passing_student / total_students) * 100
math_passing_percent= (number_of_math_passing_student / total_students) * 100


# percent of passing reading
number_of_reading_passing_student= merged_district[merged_district["reading_score"] > 70].count()["school name"]
number_of_reading_passing_student
merged_district["reading_passing_%"]= (number_of_reading_passing_student/total_students) * 100
reading_passing_percent= (number_of_reading_passing_student/total_students) * 100


# Overall Passing Rate (Average of the above two)
overall_passing_rate= (math_passing_percent + reading_passing_percent) /2
merged_district["Overall_passing_%"] =overall_passing_rate


district_data= merged_district.loc[0,["type","Total_budget","budget per student","Total_number_of_schools","Total_number_of_students",
                                     "average_math_score","average_reading_score","math_passing_%","reading_passing_%",
                                     "Overall_passing_%"]]
                                   
# district 
district_data= pd.DataFrame(district_data) 
district_data


```

    /Users/tarekmagdyshehatamohamed/miniconda3/envs/bioinfo/lib/python3.6/site-packages/ipykernel_launcher.py:5: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      """
    /Users/tarekmagdyshehatamohamed/miniconda3/envs/bioinfo/lib/python3.6/site-packages/ipykernel_launcher.py:9: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      if __name__ == '__main__':
    /Users/tarekmagdyshehatamohamed/miniconda3/envs/bioinfo/lib/python3.6/site-packages/ipykernel_launcher.py:12: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      if sys.path[0] == '':
    /Users/tarekmagdyshehatamohamed/miniconda3/envs/bioinfo/lib/python3.6/site-packages/ipykernel_launcher.py:16: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      app.launch_new_instance()
    /Users/tarekmagdyshehatamohamed/miniconda3/envs/bioinfo/lib/python3.6/site-packages/ipykernel_launcher.py:19: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
    /Users/tarekmagdyshehatamohamed/miniconda3/envs/bioinfo/lib/python3.6/site-packages/ipykernel_launcher.py:20: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>type</th>
      <td>District</td>
    </tr>
    <tr>
      <th>Total_budget</th>
      <td>17347923</td>
    </tr>
    <tr>
      <th>budget per student</th>
      <td>643.087</td>
    </tr>
    <tr>
      <th>Total_number_of_schools</th>
      <td>7</td>
    </tr>
    <tr>
      <th>Total_number_of_students</th>
      <td>26976</td>
    </tr>
    <tr>
      <th>average_math_score</th>
      <td>76.987</td>
    </tr>
    <tr>
      <th>average_reading_score</th>
      <td>80.9625</td>
    </tr>
    <tr>
      <th>math_passing_%</th>
      <td>64.3053</td>
    </tr>
    <tr>
      <th>reading_passing_%</th>
      <td>78.3697</td>
    </tr>
    <tr>
      <th>Overall_passing_%</th>
      <td>71.3375</td>
    </tr>
  </tbody>
</table>
</div>



 <font color='green'>Create school summary</font>


```python
# Other requirments
grp = merged.groupby(['school name'])
budget=grp["budget"].unique()
num_students=grp["size"].unique()
budget_per_student= budget / num_students
school_type=grp["type"].unique()
reading_score=grp["reading_score"].mean()
math_score=grp["math_score"].mean()


#math_passing_percent by school
grp02=merged.loc[(merged["math_score"] > 70)]
grp02= grp02.groupby(["school name"])
number_of_student_passed_math =grp02["math_score"].count()
number_of_student_passed_math
math_passing_percent= (number_of_student_passed_math / num_students) *100
#math_passing_percent

#reading_passing_percent by school
grp03=merged.loc[(merged["reading_score"] > 70)]
grp03= grp03.groupby(["school name"])
number_of_student_passed_reading =grp03["reading_score"].count()
number_of_student_passed_reading
reading_passing_percent= (number_of_student_passed_reading / num_students) *100
#reading_passing_percent

# overall passing rate
overall_passing_rate = (math_passing_percent + reading_passing_percent) /2
#overall_passing_rate


```


```python
school_data=pd.DataFrame({"Total budget" :budget,"number of student":num_students, 
                          "budget per student" : budget_per_student,
                          "type of school":school_type, "average reading score": reading_score,
                          "average math score":math_score, "reading passing %": reading_passing_percent, 
                          "math passing %": math_passing_percent,"overall passing rate":overall_passing_rate} )

school_data = school_data[["type of school","Total budget","number of student","budget per student",
                           "average reading score","average math score", "reading passing %", "math passing %","overall passing rate" ]]
school_data

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type of school</th>
      <th>Total budget</th>
      <th>number of student</th>
      <th>budget per student</th>
      <th>average reading score</th>
      <th>average math score</th>
      <th>reading passing %</th>
      <th>math passing %</th>
      <th>overall passing rate</th>
    </tr>
    <tr>
      <th>school name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>[District]</td>
      <td>[3124928]</td>
      <td>[4976]</td>
      <td>[628.0]</td>
      <td>81.033963</td>
      <td>77.048432</td>
      <td>[79.3006430868]</td>
      <td>[64.6302250804]</td>
      <td>[71.9654340836]</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>[Charter]</td>
      <td>[1081356]</td>
      <td>[1858]</td>
      <td>[582.0]</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>[93.8643702906]</td>
      <td>[89.5586652314]</td>
      <td>[91.711517761]</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>[District]</td>
      <td>[1884411]</td>
      <td>[2949]</td>
      <td>[639.0]</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>[78.4333672431]</td>
      <td>[63.7504238725]</td>
      <td>[71.0918955578]</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>[District]</td>
      <td>[1763916]</td>
      <td>[2739]</td>
      <td>[644.0]</td>
      <td>80.746258</td>
      <td>77.102592</td>
      <td>[77.5100401606]</td>
      <td>[65.7539247901]</td>
      <td>[71.6319824754]</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>[Charter]</td>
      <td>[917500]</td>
      <td>[1468]</td>
      <td>[625.0]</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>[93.3923705722]</td>
      <td>[89.7138964578]</td>
      <td>[91.553133515]</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>[District]</td>
      <td>[3022020]</td>
      <td>[4635]</td>
      <td>[652.0]</td>
      <td>80.934412</td>
      <td>77.289752</td>
      <td>[78.1877022654]</td>
      <td>[64.7464940669]</td>
      <td>[71.4670981661]</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>[Charter]</td>
      <td>[248087]</td>
      <td>[427]</td>
      <td>[581.0]</td>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>[92.7400468384]</td>
      <td>[90.6323185012]</td>
      <td>[91.6861826698]</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>[District]</td>
      <td>[1910635]</td>
      <td>[2917]</td>
      <td>[655.0]</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>[78.8138498457]</td>
      <td>[63.3184778882]</td>
      <td>[71.066163867]</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>[District]</td>
      <td>[3094650]</td>
      <td>[4761]</td>
      <td>[650.0]</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>[78.281873556]</td>
      <td>[63.8521319051]</td>
      <td>[71.0670027305]</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>[Charter]</td>
      <td>[585858]</td>
      <td>[962]</td>
      <td>[609.0]</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>[92.2037422037]</td>
      <td>[91.683991684]</td>
      <td>[91.9438669439]</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>[District]</td>
      <td>[2547363]</td>
      <td>[3999]</td>
      <td>[637.0]</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>[77.744436109]</td>
      <td>[64.0660165041]</td>
      <td>[70.9052263066]</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>[Charter]</td>
      <td>[1056600]</td>
      <td>[1761]</td>
      <td>[600.0]</td>
      <td>83.725724</td>
      <td>83.359455</td>
      <td>[92.617830778]</td>
      <td>[89.8921067575]</td>
      <td>[91.2549687677]</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>[Charter]</td>
      <td>[1043130]</td>
      <td>[1635]</td>
      <td>[638.0]</td>
      <td>83.848930</td>
      <td>83.418349</td>
      <td>[92.9051987768]</td>
      <td>[90.2140672783]</td>
      <td>[91.5596330275]</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>[Charter]</td>
      <td>[1319574]</td>
      <td>[2283]</td>
      <td>[578.0]</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>[93.2544897065]</td>
      <td>[90.9329829172]</td>
      <td>[92.0937363119]</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>[Charter]</td>
      <td>[1049400]</td>
      <td>[1800]</td>
      <td>[583.0]</td>
      <td>83.955000</td>
      <td>83.682222</td>
      <td>[93.4444444444]</td>
      <td>[90.2777777778]</td>
      <td>[91.8611111111]</td>
    </tr>
  </tbody>
</table>
</div>



 <font color='green'>Top five performing schools</font>


```python
#schools sorted by overall passing rate
school_sorted=school_data.sort_values("overall passing rate", ascending=False)
school_sorted
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type of school</th>
      <th>Total budget</th>
      <th>number of student</th>
      <th>budget per student</th>
      <th>average reading score</th>
      <th>average math score</th>
      <th>reading passing %</th>
      <th>math passing %</th>
      <th>overall passing rate</th>
    </tr>
    <tr>
      <th>school name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Wilson High School</th>
      <td>[Charter]</td>
      <td>[1319574]</td>
      <td>[2283]</td>
      <td>[578.0]</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>[93.2544897065]</td>
      <td>[90.9329829172]</td>
      <td>[92.0937363119]</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>[Charter]</td>
      <td>[585858]</td>
      <td>[962]</td>
      <td>[609.0]</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>[92.2037422037]</td>
      <td>[91.683991684]</td>
      <td>[91.9438669439]</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>[Charter]</td>
      <td>[1049400]</td>
      <td>[1800]</td>
      <td>[583.0]</td>
      <td>83.955000</td>
      <td>83.682222</td>
      <td>[93.4444444444]</td>
      <td>[90.2777777778]</td>
      <td>[91.8611111111]</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>[Charter]</td>
      <td>[1081356]</td>
      <td>[1858]</td>
      <td>[582.0]</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>[93.8643702906]</td>
      <td>[89.5586652314]</td>
      <td>[91.711517761]</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>[Charter]</td>
      <td>[248087]</td>
      <td>[427]</td>
      <td>[581.0]</td>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>[92.7400468384]</td>
      <td>[90.6323185012]</td>
      <td>[91.6861826698]</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>[Charter]</td>
      <td>[1043130]</td>
      <td>[1635]</td>
      <td>[638.0]</td>
      <td>83.848930</td>
      <td>83.418349</td>
      <td>[92.9051987768]</td>
      <td>[90.2140672783]</td>
      <td>[91.5596330275]</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>[Charter]</td>
      <td>[917500]</td>
      <td>[1468]</td>
      <td>[625.0]</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>[93.3923705722]</td>
      <td>[89.7138964578]</td>
      <td>[91.553133515]</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>[Charter]</td>
      <td>[1056600]</td>
      <td>[1761]</td>
      <td>[600.0]</td>
      <td>83.725724</td>
      <td>83.359455</td>
      <td>[92.617830778]</td>
      <td>[89.8921067575]</td>
      <td>[91.2549687677]</td>
    </tr>
    <tr>
      <th>Bailey High School</th>
      <td>[District]</td>
      <td>[3124928]</td>
      <td>[4976]</td>
      <td>[628.0]</td>
      <td>81.033963</td>
      <td>77.048432</td>
      <td>[79.3006430868]</td>
      <td>[64.6302250804]</td>
      <td>[71.9654340836]</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>[District]</td>
      <td>[1763916]</td>
      <td>[2739]</td>
      <td>[644.0]</td>
      <td>80.746258</td>
      <td>77.102592</td>
      <td>[77.5100401606]</td>
      <td>[65.7539247901]</td>
      <td>[71.6319824754]</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>[District]</td>
      <td>[3022020]</td>
      <td>[4635]</td>
      <td>[652.0]</td>
      <td>80.934412</td>
      <td>77.289752</td>
      <td>[78.1877022654]</td>
      <td>[64.7464940669]</td>
      <td>[71.4670981661]</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>[District]</td>
      <td>[1884411]</td>
      <td>[2949]</td>
      <td>[639.0]</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>[78.4333672431]</td>
      <td>[63.7504238725]</td>
      <td>[71.0918955578]</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>[District]</td>
      <td>[3094650]</td>
      <td>[4761]</td>
      <td>[650.0]</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>[78.281873556]</td>
      <td>[63.8521319051]</td>
      <td>[71.0670027305]</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>[District]</td>
      <td>[1910635]</td>
      <td>[2917]</td>
      <td>[655.0]</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>[78.8138498457]</td>
      <td>[63.3184778882]</td>
      <td>[71.066163867]</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>[District]</td>
      <td>[2547363]</td>
      <td>[3999]</td>
      <td>[637.0]</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>[77.744436109]</td>
      <td>[64.0660165041]</td>
      <td>[70.9052263066]</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Top five Performing Schools (By Passing Rate)
school_sorted=school_data.sort_values("overall passing rate", ascending=False)
school_sorted
Top_five_school= school_sorted.iloc[0:5,:]
Top_five_school
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type of school</th>
      <th>Total budget</th>
      <th>number of student</th>
      <th>budget per student</th>
      <th>average reading score</th>
      <th>average math score</th>
      <th>reading passing %</th>
      <th>math passing %</th>
      <th>overall passing rate</th>
    </tr>
    <tr>
      <th>school name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Wilson High School</th>
      <td>[Charter]</td>
      <td>[1319574]</td>
      <td>[2283]</td>
      <td>[578.0]</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>[93.2544897065]</td>
      <td>[90.9329829172]</td>
      <td>[92.0937363119]</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>[Charter]</td>
      <td>[585858]</td>
      <td>[962]</td>
      <td>[609.0]</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>[92.2037422037]</td>
      <td>[91.683991684]</td>
      <td>[91.9438669439]</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>[Charter]</td>
      <td>[1049400]</td>
      <td>[1800]</td>
      <td>[583.0]</td>
      <td>83.955000</td>
      <td>83.682222</td>
      <td>[93.4444444444]</td>
      <td>[90.2777777778]</td>
      <td>[91.8611111111]</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>[Charter]</td>
      <td>[1081356]</td>
      <td>[1858]</td>
      <td>[582.0]</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>[93.8643702906]</td>
      <td>[89.5586652314]</td>
      <td>[91.711517761]</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>[Charter]</td>
      <td>[248087]</td>
      <td>[427]</td>
      <td>[581.0]</td>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>[92.7400468384]</td>
      <td>[90.6323185012]</td>
      <td>[91.6861826698]</td>
    </tr>
  </tbody>
</table>
</div>



 <font color='green'>Bottom five performing schools</font>


```python
#Bottom five performing schools sorted by overall passing rate
school_sorted=school_data.sort_values("overall passing rate")
school_sorted
Bottom_five_school= school_sorted.iloc[0:5,:]
Bottom_five_school
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type of school</th>
      <th>Total budget</th>
      <th>number of student</th>
      <th>budget per student</th>
      <th>average reading score</th>
      <th>average math score</th>
      <th>reading passing %</th>
      <th>math passing %</th>
      <th>overall passing rate</th>
    </tr>
    <tr>
      <th>school name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Rodriguez High School</th>
      <td>[District]</td>
      <td>[2547363]</td>
      <td>[3999]</td>
      <td>[637.0]</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>[77.744436109]</td>
      <td>[64.0660165041]</td>
      <td>[70.9052263066]</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>[District]</td>
      <td>[1910635]</td>
      <td>[2917]</td>
      <td>[655.0]</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>[78.8138498457]</td>
      <td>[63.3184778882]</td>
      <td>[71.066163867]</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>[District]</td>
      <td>[3094650]</td>
      <td>[4761]</td>
      <td>[650.0]</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>[78.281873556]</td>
      <td>[63.8521319051]</td>
      <td>[71.0670027305]</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>[District]</td>
      <td>[1884411]</td>
      <td>[2949]</td>
      <td>[639.0]</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>[78.4333672431]</td>
      <td>[63.7504238725]</td>
      <td>[71.0918955578]</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>[District]</td>
      <td>[3022020]</td>
      <td>[4635]</td>
      <td>[652.0]</td>
      <td>80.934412</td>
      <td>77.289752</td>
      <td>[78.1877022654]</td>
      <td>[64.7464940669]</td>
      <td>[71.4670981661]</td>
    </tr>
  </tbody>
</table>
</div>




```python
school_sorted_budget=school_data.sort_values("budget per student", ascending=False)
school_sorted_budget


```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type of school</th>
      <th>Total budget</th>
      <th>number of student</th>
      <th>budget per student</th>
      <th>average reading score</th>
      <th>average math score</th>
      <th>reading passing %</th>
      <th>math passing %</th>
      <th>overall passing rate</th>
    </tr>
    <tr>
      <th>school name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Huang High School</th>
      <td>[District]</td>
      <td>[1910635]</td>
      <td>[2917]</td>
      <td>[655.0]</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>[78.8138498457]</td>
      <td>[63.3184778882]</td>
      <td>[71.066163867]</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>[District]</td>
      <td>[3022020]</td>
      <td>[4635]</td>
      <td>[652.0]</td>
      <td>80.934412</td>
      <td>77.289752</td>
      <td>[78.1877022654]</td>
      <td>[64.7464940669]</td>
      <td>[71.4670981661]</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>[District]</td>
      <td>[3094650]</td>
      <td>[4761]</td>
      <td>[650.0]</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>[78.281873556]</td>
      <td>[63.8521319051]</td>
      <td>[71.0670027305]</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>[District]</td>
      <td>[1763916]</td>
      <td>[2739]</td>
      <td>[644.0]</td>
      <td>80.746258</td>
      <td>77.102592</td>
      <td>[77.5100401606]</td>
      <td>[65.7539247901]</td>
      <td>[71.6319824754]</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>[District]</td>
      <td>[1884411]</td>
      <td>[2949]</td>
      <td>[639.0]</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>[78.4333672431]</td>
      <td>[63.7504238725]</td>
      <td>[71.0918955578]</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>[Charter]</td>
      <td>[1043130]</td>
      <td>[1635]</td>
      <td>[638.0]</td>
      <td>83.848930</td>
      <td>83.418349</td>
      <td>[92.9051987768]</td>
      <td>[90.2140672783]</td>
      <td>[91.5596330275]</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>[District]</td>
      <td>[2547363]</td>
      <td>[3999]</td>
      <td>[637.0]</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>[77.744436109]</td>
      <td>[64.0660165041]</td>
      <td>[70.9052263066]</td>
    </tr>
    <tr>
      <th>Bailey High School</th>
      <td>[District]</td>
      <td>[3124928]</td>
      <td>[4976]</td>
      <td>[628.0]</td>
      <td>81.033963</td>
      <td>77.048432</td>
      <td>[79.3006430868]</td>
      <td>[64.6302250804]</td>
      <td>[71.9654340836]</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>[Charter]</td>
      <td>[917500]</td>
      <td>[1468]</td>
      <td>[625.0]</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>[93.3923705722]</td>
      <td>[89.7138964578]</td>
      <td>[91.553133515]</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>[Charter]</td>
      <td>[585858]</td>
      <td>[962]</td>
      <td>[609.0]</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>[92.2037422037]</td>
      <td>[91.683991684]</td>
      <td>[91.9438669439]</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>[Charter]</td>
      <td>[1056600]</td>
      <td>[1761]</td>
      <td>[600.0]</td>
      <td>83.725724</td>
      <td>83.359455</td>
      <td>[92.617830778]</td>
      <td>[89.8921067575]</td>
      <td>[91.2549687677]</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>[Charter]</td>
      <td>[1049400]</td>
      <td>[1800]</td>
      <td>[583.0]</td>
      <td>83.955000</td>
      <td>83.682222</td>
      <td>[93.4444444444]</td>
      <td>[90.2777777778]</td>
      <td>[91.8611111111]</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>[Charter]</td>
      <td>[1081356]</td>
      <td>[1858]</td>
      <td>[582.0]</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>[93.8643702906]</td>
      <td>[89.5586652314]</td>
      <td>[91.711517761]</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>[Charter]</td>
      <td>[248087]</td>
      <td>[427]</td>
      <td>[581.0]</td>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>[92.7400468384]</td>
      <td>[90.6323185012]</td>
      <td>[91.6861826698]</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>[Charter]</td>
      <td>[1319574]</td>
      <td>[2283]</td>
      <td>[578.0]</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>[93.2544897065]</td>
      <td>[90.9329829172]</td>
      <td>[92.0937363119]</td>
    </tr>
  </tbody>
</table>
</div>



 <font color='green'>schools by budget per studen</font>


```python
#school scores by budget per student
bins = [0, 600, 630, 700]
group_names = ['low', 'moderate', 'high']
school_sorted_budget["budget per student group"] =pd.cut(school_sorted_budget["budget per student"], bins, labels = group_names)
school_sorted_budget_final = school_sorted_budget.drop(columns=["type of school", "number of student", "Total budget"])
school_sorted_budget_final

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>budget per student</th>
      <th>average reading score</th>
      <th>average math score</th>
      <th>reading passing %</th>
      <th>math passing %</th>
      <th>overall passing rate</th>
      <th>budget per student group</th>
    </tr>
    <tr>
      <th>school name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Huang High School</th>
      <td>[655.0]</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>[78.8138498457]</td>
      <td>[63.3184778882]</td>
      <td>[71.066163867]</td>
      <td>high</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>[652.0]</td>
      <td>80.934412</td>
      <td>77.289752</td>
      <td>[78.1877022654]</td>
      <td>[64.7464940669]</td>
      <td>[71.4670981661]</td>
      <td>high</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>[650.0]</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>[78.281873556]</td>
      <td>[63.8521319051]</td>
      <td>[71.0670027305]</td>
      <td>high</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>[644.0]</td>
      <td>80.746258</td>
      <td>77.102592</td>
      <td>[77.5100401606]</td>
      <td>[65.7539247901]</td>
      <td>[71.6319824754]</td>
      <td>high</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>[639.0]</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>[78.4333672431]</td>
      <td>[63.7504238725]</td>
      <td>[71.0918955578]</td>
      <td>high</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>[638.0]</td>
      <td>83.848930</td>
      <td>83.418349</td>
      <td>[92.9051987768]</td>
      <td>[90.2140672783]</td>
      <td>[91.5596330275]</td>
      <td>high</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>[637.0]</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>[77.744436109]</td>
      <td>[64.0660165041]</td>
      <td>[70.9052263066]</td>
      <td>high</td>
    </tr>
    <tr>
      <th>Bailey High School</th>
      <td>[628.0]</td>
      <td>81.033963</td>
      <td>77.048432</td>
      <td>[79.3006430868]</td>
      <td>[64.6302250804]</td>
      <td>[71.9654340836]</td>
      <td>moderate</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>[625.0]</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>[93.3923705722]</td>
      <td>[89.7138964578]</td>
      <td>[91.553133515]</td>
      <td>moderate</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>[609.0]</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>[92.2037422037]</td>
      <td>[91.683991684]</td>
      <td>[91.9438669439]</td>
      <td>moderate</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>[600.0]</td>
      <td>83.725724</td>
      <td>83.359455</td>
      <td>[92.617830778]</td>
      <td>[89.8921067575]</td>
      <td>[91.2549687677]</td>
      <td>low</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>[583.0]</td>
      <td>83.955000</td>
      <td>83.682222</td>
      <td>[93.4444444444]</td>
      <td>[90.2777777778]</td>
      <td>[91.8611111111]</td>
      <td>low</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>[582.0]</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>[93.8643702906]</td>
      <td>[89.5586652314]</td>
      <td>[91.711517761]</td>
      <td>low</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>[581.0]</td>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>[92.7400468384]</td>
      <td>[90.6323185012]</td>
      <td>[91.6861826698]</td>
      <td>low</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>[578.0]</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>[93.2544897065]</td>
      <td>[90.9329829172]</td>
      <td>[92.0937363119]</td>
      <td>low</td>
    </tr>
  </tbody>
</table>
</div>




```python
school_sorted_size=school_data.sort_values("number of student", ascending=False)
school_sorted_size

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type of school</th>
      <th>Total budget</th>
      <th>number of student</th>
      <th>budget per student</th>
      <th>average reading score</th>
      <th>average math score</th>
      <th>reading passing %</th>
      <th>math passing %</th>
      <th>overall passing rate</th>
    </tr>
    <tr>
      <th>school name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>[District]</td>
      <td>[3124928]</td>
      <td>[4976]</td>
      <td>[628.0]</td>
      <td>81.033963</td>
      <td>77.048432</td>
      <td>[79.3006430868]</td>
      <td>[64.6302250804]</td>
      <td>[71.9654340836]</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>[District]</td>
      <td>[3094650]</td>
      <td>[4761]</td>
      <td>[650.0]</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>[78.281873556]</td>
      <td>[63.8521319051]</td>
      <td>[71.0670027305]</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>[District]</td>
      <td>[3022020]</td>
      <td>[4635]</td>
      <td>[652.0]</td>
      <td>80.934412</td>
      <td>77.289752</td>
      <td>[78.1877022654]</td>
      <td>[64.7464940669]</td>
      <td>[71.4670981661]</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>[District]</td>
      <td>[2547363]</td>
      <td>[3999]</td>
      <td>[637.0]</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>[77.744436109]</td>
      <td>[64.0660165041]</td>
      <td>[70.9052263066]</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>[District]</td>
      <td>[1884411]</td>
      <td>[2949]</td>
      <td>[639.0]</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>[78.4333672431]</td>
      <td>[63.7504238725]</td>
      <td>[71.0918955578]</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>[District]</td>
      <td>[1910635]</td>
      <td>[2917]</td>
      <td>[655.0]</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>[78.8138498457]</td>
      <td>[63.3184778882]</td>
      <td>[71.066163867]</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>[District]</td>
      <td>[1763916]</td>
      <td>[2739]</td>
      <td>[644.0]</td>
      <td>80.746258</td>
      <td>77.102592</td>
      <td>[77.5100401606]</td>
      <td>[65.7539247901]</td>
      <td>[71.6319824754]</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>[Charter]</td>
      <td>[1319574]</td>
      <td>[2283]</td>
      <td>[578.0]</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>[93.2544897065]</td>
      <td>[90.9329829172]</td>
      <td>[92.0937363119]</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>[Charter]</td>
      <td>[1081356]</td>
      <td>[1858]</td>
      <td>[582.0]</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>[93.8643702906]</td>
      <td>[89.5586652314]</td>
      <td>[91.711517761]</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>[Charter]</td>
      <td>[1049400]</td>
      <td>[1800]</td>
      <td>[583.0]</td>
      <td>83.955000</td>
      <td>83.682222</td>
      <td>[93.4444444444]</td>
      <td>[90.2777777778]</td>
      <td>[91.8611111111]</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>[Charter]</td>
      <td>[1056600]</td>
      <td>[1761]</td>
      <td>[600.0]</td>
      <td>83.725724</td>
      <td>83.359455</td>
      <td>[92.617830778]</td>
      <td>[89.8921067575]</td>
      <td>[91.2549687677]</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>[Charter]</td>
      <td>[1043130]</td>
      <td>[1635]</td>
      <td>[638.0]</td>
      <td>83.848930</td>
      <td>83.418349</td>
      <td>[92.9051987768]</td>
      <td>[90.2140672783]</td>
      <td>[91.5596330275]</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>[Charter]</td>
      <td>[917500]</td>
      <td>[1468]</td>
      <td>[625.0]</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>[93.3923705722]</td>
      <td>[89.7138964578]</td>
      <td>[91.553133515]</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>[Charter]</td>
      <td>[585858]</td>
      <td>[962]</td>
      <td>[609.0]</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>[92.2037422037]</td>
      <td>[91.683991684]</td>
      <td>[91.9438669439]</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>[Charter]</td>
      <td>[248087]</td>
      <td>[427]</td>
      <td>[581.0]</td>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>[92.7400468384]</td>
      <td>[90.6323185012]</td>
      <td>[91.6861826698]</td>
    </tr>
  </tbody>
</table>
</div>



 <font color='green'>schools by number of students</font>


```python
#school scores by  size (number of students)

bins = [0, 1000, 2000, 5000]
group_names = ['small', 'medium', 'large']
school_sorted_size["size group"] =pd.cut(school_sorted_size["number of student"], bins, labels = group_names)
school_sorted_size
school_sorted_size_final = school_sorted_size.drop(columns=["type of school", "budget per student", "Total budget"])
school_sorted_size_final
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>number of student</th>
      <th>average reading score</th>
      <th>average math score</th>
      <th>reading passing %</th>
      <th>math passing %</th>
      <th>overall passing rate</th>
      <th>size group</th>
    </tr>
    <tr>
      <th>school name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>[4976]</td>
      <td>81.033963</td>
      <td>77.048432</td>
      <td>[79.3006430868]</td>
      <td>[64.6302250804]</td>
      <td>[71.9654340836]</td>
      <td>large</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>[4761]</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>[78.281873556]</td>
      <td>[63.8521319051]</td>
      <td>[71.0670027305]</td>
      <td>large</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>[4635]</td>
      <td>80.934412</td>
      <td>77.289752</td>
      <td>[78.1877022654]</td>
      <td>[64.7464940669]</td>
      <td>[71.4670981661]</td>
      <td>large</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>[3999]</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>[77.744436109]</td>
      <td>[64.0660165041]</td>
      <td>[70.9052263066]</td>
      <td>large</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>[2949]</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>[78.4333672431]</td>
      <td>[63.7504238725]</td>
      <td>[71.0918955578]</td>
      <td>large</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>[2917]</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>[78.8138498457]</td>
      <td>[63.3184778882]</td>
      <td>[71.066163867]</td>
      <td>large</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>[2739]</td>
      <td>80.746258</td>
      <td>77.102592</td>
      <td>[77.5100401606]</td>
      <td>[65.7539247901]</td>
      <td>[71.6319824754]</td>
      <td>large</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>[2283]</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>[93.2544897065]</td>
      <td>[90.9329829172]</td>
      <td>[92.0937363119]</td>
      <td>large</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>[1858]</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>[93.8643702906]</td>
      <td>[89.5586652314]</td>
      <td>[91.711517761]</td>
      <td>medium</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>[1800]</td>
      <td>83.955000</td>
      <td>83.682222</td>
      <td>[93.4444444444]</td>
      <td>[90.2777777778]</td>
      <td>[91.8611111111]</td>
      <td>medium</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>[1761]</td>
      <td>83.725724</td>
      <td>83.359455</td>
      <td>[92.617830778]</td>
      <td>[89.8921067575]</td>
      <td>[91.2549687677]</td>
      <td>medium</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>[1635]</td>
      <td>83.848930</td>
      <td>83.418349</td>
      <td>[92.9051987768]</td>
      <td>[90.2140672783]</td>
      <td>[91.5596330275]</td>
      <td>medium</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>[1468]</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>[93.3923705722]</td>
      <td>[89.7138964578]</td>
      <td>[91.553133515]</td>
      <td>medium</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>[962]</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>[92.2037422037]</td>
      <td>[91.683991684]</td>
      <td>[91.9438669439]</td>
      <td>small</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>[427]</td>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>[92.7400468384]</td>
      <td>[90.6323185012]</td>
      <td>[91.6861826698]</td>
      <td>small</td>
    </tr>
  </tbody>
</table>
</div>



 <font color='green'>schools by type</font>


```python
#school scores by  type (district_vs_charter)
district_vs_charter= school_data.drop(columns=["number of student", "budget per student", "Total budget"])
district_vs_charter.sort_values("type of school")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type of school</th>
      <th>average reading score</th>
      <th>average math score</th>
      <th>reading passing %</th>
      <th>math passing %</th>
      <th>overall passing rate</th>
    </tr>
    <tr>
      <th>school name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Cabrera High School</th>
      <td>[Charter]</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>[93.8643702906]</td>
      <td>[89.5586652314]</td>
      <td>[91.711517761]</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>[Charter]</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>[93.3923705722]</td>
      <td>[89.7138964578]</td>
      <td>[91.553133515]</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>[Charter]</td>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>[92.7400468384]</td>
      <td>[90.6323185012]</td>
      <td>[91.6861826698]</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>[Charter]</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>[92.2037422037]</td>
      <td>[91.683991684]</td>
      <td>[91.9438669439]</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>[Charter]</td>
      <td>83.725724</td>
      <td>83.359455</td>
      <td>[92.617830778]</td>
      <td>[89.8921067575]</td>
      <td>[91.2549687677]</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>[Charter]</td>
      <td>83.848930</td>
      <td>83.418349</td>
      <td>[92.9051987768]</td>
      <td>[90.2140672783]</td>
      <td>[91.5596330275]</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>[Charter]</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>[93.2544897065]</td>
      <td>[90.9329829172]</td>
      <td>[92.0937363119]</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>[Charter]</td>
      <td>83.955000</td>
      <td>83.682222</td>
      <td>[93.4444444444]</td>
      <td>[90.2777777778]</td>
      <td>[91.8611111111]</td>
    </tr>
    <tr>
      <th>Bailey High School</th>
      <td>[District]</td>
      <td>81.033963</td>
      <td>77.048432</td>
      <td>[79.3006430868]</td>
      <td>[64.6302250804]</td>
      <td>[71.9654340836]</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>[District]</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>[78.4333672431]</td>
      <td>[63.7504238725]</td>
      <td>[71.0918955578]</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>[District]</td>
      <td>80.746258</td>
      <td>77.102592</td>
      <td>[77.5100401606]</td>
      <td>[65.7539247901]</td>
      <td>[71.6319824754]</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>[District]</td>
      <td>80.934412</td>
      <td>77.289752</td>
      <td>[78.1877022654]</td>
      <td>[64.7464940669]</td>
      <td>[71.4670981661]</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>[District]</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>[78.8138498457]</td>
      <td>[63.3184778882]</td>
      <td>[71.066163867]</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>[District]</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>[78.281873556]</td>
      <td>[63.8521319051]</td>
      <td>[71.0670027305]</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>[District]</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>[77.744436109]</td>
      <td>[64.0660165041]</td>
      <td>[70.9052263066]</td>
    </tr>
  </tbody>
</table>
</div>




```python



```


```python


```


```python



```


```python




```
