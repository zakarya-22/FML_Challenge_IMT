# Document to share the findings of the initial analysis

## Dataset

### Bike Types

- A total of 121 different bike types
- 30 bikes have missing names
- 30 bikes have missing rider capacity
- 30 bikes have missing name, propulsion types etc
- 22 bike types have battery capacity but only 15 have max range, so would need to fill in the values.
- Only 10 bike types have all the information
- There are 27 electric bikes and 64 human but only 22 have battery capacity maybe, we need to check this too
    - max_range           12
    - battery_capacity     5
- I guess there are only 92 unique bikes or maybe some bikes with wrong pictures as running `len(bike_types['vehicle_image'].unique())` returns 92.
- Not all bike types have descriptions but i guess that is fine

Questions:

- What should we use as a tie breaker to find duplicates? 
    - Fuzzy search on name and description while also using propulsion type, rider capacity and form factor
    - image link
