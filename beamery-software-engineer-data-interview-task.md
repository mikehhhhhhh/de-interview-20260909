# Beamery - Software Engineer (Data) - Technical Interview Task

You work as an engineer for HR Startup Inc, a company that builds a Software-as-a-Service (SaaS) product for companies
to manage their recruitment pipelines. Your customers are interested in knowing how many candidates that apply to their
vacancies would have to relocate if they got the job. The product team has decided it would be useful to show a pie
chart in the app showing what proportion of applicants in a given year would have required relocation.

You have been provided with a CSV file containing a list of candidates who have applied for jobs at a particular
customer.

The `candidates.csv` contains the following columns:

- `candidate_id` - string field with the id for a candidate
- `location` - string field with the location of the candidate, in the form City - Country
- `vacancy_id` - string field with the id of the vacancy the candidate applied for
- `applied_at` - string in the format YYYY-MM-DD. The date the candidate applied to the vacancy.

You have also been provided with a CSV file, `vacancies.csv`, containing information about the vacancies the customer has
hired for:

- `vacancy_id` - string field with the id of the vacancy
- `location` - string field with the location of the vacancy, in the form City - Country
- `name` - string field with the name of the vacancy

Please develop a method which will enable the app to look up the total number of applicants in a given year, and
the total number of applicants who would require relocation in that year. This could take the form of a function,
a HTTP API, or any other approach which you think is appropriate.

---

So for example if we had the following candidates:
```
candidate-1,London - UK,vacancy-1,2022-02-03
candidate-2,Paris - France,vacancy-1,2022-04-03
candidate-3,Mumbai - India,vacancy-2,2022-11-29
candidate-4,New York - US,vacancy-2,2022-12-02
candidate-5,New York - US,vacancy-2,2023-01-05
```

And the following vacancies:
```
vacancy-1,London - UK,Software Engineer
vacancy-2,New York - US,Head of Product
```

If we execute function with an argument of 2022, we would expect it to return 4 for the total number of
applicants and 2 for the total number of applicants requiring relocation. To explain:

- `candidate-1` applied in 2022 and is located in London and is applying for a vacancy in London. They count towards total
applications but not the applications who would require relocation.

- `candidate-2` applied in 2022 and is located in Paris and is applying for a vacancy in London. They count towards total
applications and towards the count of applications that would require relocation.

- `candidate-3` applied in 2022 from Mumbai for a vacancy in New York. They count towards total and relocations.

- `candidate-4` applied in 2022 from New York for a vacancy in New York. Counts towards total but not relocations.

- `candidate-5` did not apply in 2022, they would not be counted when the endpoint is queried with the year of 2022.
