# Colorado Department of Revenue Salaries

Salaries of state employees in Colorado are public record, so out of curiousity
I requested the salaries of the employees of the Colorado Department of Revenue.

This includes:
  
  - Colorado Lottery
  - Division of Motor Vehicles
  - Taxation Division
  - Enforcement Division
      - Auto Industry
      - Gaming
      - Hearings
      - Liquor and Tobacco
      - Marijuana
      - Racing


This repository contains:

- `DOR_Total_Earnings.pdf`, the data exactly as it was provided, in case the
  parsing script was incorrect.

  > The information contained in this report reflects actual earnings
  > for all permanent and temporary personnel. The amounts include all
  > pay types (regular pay, shift differential, overtime, etc). In
  > order for the department to provide the information at no cost, no
  > adjustments were made for personnel paid by more than one funding
  > source, therefore, a name may appear more than once.

- `salaries.sql`, the salary data as a sql dump to be loaded into sqlite. Be
  aware that each row does not represent the total salary per year, in cases
  where an employee is paid through multiple funding sources.

- [`salaries.csv`](salaries.csv), the normalized salaries as CSV.
  This one has all the funding sources combined, so it really is total
  compensation per year.


## Interesting queries

To load the data into sqlite to play with yourself, run

    sqlite somename.db < salaries.sql

Then do `sqlite somename.db` to get into a sql shell.

To get total salary per year, try

    SELECT year, name, SUM(salary) FROM salaries GROUP BY year, name;
