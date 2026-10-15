# Document to share the findings of the initial analysis

## Dataset

### Bike Types

- A total of 121 different bike types
- 30 bikes have missing name, desc, range, propulsioon type, battery cap
- 22 bike types have battery capacity but only 15 have max range, so would need to fill in the values.
- Only 10 bike types have all the information
- There are 27 electric bikes and 64 human but only 22 have battery capacity maybe, we need to check this too
    - max_range           12
    - battery_capacity     5
- Not all bike types have descriptions but i guess that is fine
- All bikes that have battery capacity have electric assist type so thats good (same for max_capacity)
- `bike_types['name'].dropna().unique()` -> There are only 46 unique bike name and even between them there are similarities like 'e-CARGObike' and 'e-Cargobike'.
- Some bikes seem to be the same but just with different advert banner in images. Is it worth it to put them as a same bike? (It would require going through the images and stuff)
- There are 51 bike descriptions and 41 unique ones (including nan), maybe it is worth combining those?
- Okay so there are no bikes that have propulsion type as null and have battery stats in trips so maybe they are all human powered
- Based on form-factor -> 91 bikes have non null values -> 71 bicycles, 19 cargo and 1 other

#### Things to fix
- Add an average or median values to the missing battery capacity and max range
- Add a separate column that would help us create cluster of similar bikes (based on propulsion type, rider cap, form factor, battery capacity, max range) as this might help to make more sense of the data (Maybe we can run a k means to find clusters within bike types?)
- Should we do something about the same/similar bikes (maybe cluster would help here too)
- For the bikes that do not have any battery data, is it safe to assume that they are human powered?
- Exclude the bike with 30 missing or mark the values as unknown and do a separate analysis with them!

### Bikes

- `bikes.isna().sum()` returns 0 - best case scenario - no nulls anywhere but need to check as there are some 0 values instead of na maybe
- All the bike type IDs in here have a corresponding entry in bike_types table so good.
- There are 5856 electric and 81530 human propelled bikes
- `bikes.query("computer_id == 0 & propulsion_type == 'electric_assist'")` 100 electric bikes with no computer IDs and 13136 in total.
- computer_id is not unique, 2879 computers are shared at least in 2 different bikes



