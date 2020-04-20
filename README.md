# Allocations for Section 18004 (a) (1) of the Cares Act 

HT: [@Oilfield_Rando](https://twitter.com/Oilfield_Rando) (pretty shamless blue checks taking his research and republishing as original).

Data from https://www2.ed.gov/about/offices/list/ope/allocationsforsection18004a1ofcaresact.pdf

- Converted to `csv` via [Tabula](https://tabula.technology)
- Cleaned up using `R`

```
df %>% 
  filter(X1 != 'Allocations for Section 18004(a)(1) of the CARES Act',
         X1 != 'OPEID') %>% 
  set_names(c('opeid','school','total','min_aid')) %>% 
  mutate(total = parse_number(total),
         min_aid = parse_number(min_aid)) %>% 
  na.omit() %>%  # drop rounding and note columns
  arrange(desc(total)) %>% 
  write_csv('allocations.csv')
```

