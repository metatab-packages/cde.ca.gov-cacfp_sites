# Child and Adult Care Food Program (CACFP) Sites

California Department of Education CACFP sites file, with extra features,
include:

* Sites geocoded to Lat/Lon and Census tract
* The `program_types` field is broken out into dummy variables
* CDS codes are matched from the CDE schools list. 

## CDS Code Matching

There are 5 different methods for matching sites to schools in the schools
file, each with its own code:

* `fhs`: Fuzzy hash string, a has string based n the address. 
* `fhs_nz`: The fuzzy hash strin, but without the zip code, which occasionally is wrong or changes. 
* `name_city`: A lightly normalized ( alpha only, lowercase, combination of the site name and the site city
* `name_county`: A lightly normalized combination of the site name and county
* `mp_name`: The site name and county, with each word converted to it's metaphone. 

The matching method code is included in the `match_type` columns. For many of
the matching types there can be more than one CDS code associated with the
matching string, particularly the strings based on addresses. The ``match_qc``
value is the inverse of the number of values with the same matching code, so if
the algorithm selected the first of 5 CDS codes, the ``match_qc`` value is .2

Only about of the 35% of the 5076 sites are matched. The number matched for each type of matching tecchnique is: 

    Not Matched    3292
    fhs            1602
    name_city       161
    name_county      19
    mp_name           1
    fhs_nz            1
    
## Versions

1. Initial version
2. Add faked CDS codes for sites that are not schools

<!-- start_license -->
## License

The source data, from the California Department of Education, does not
explicitly reference a license, but since the top-level website for California
indicates that data published on the State of California website [is
generally in the public domain](https://www.ca.gov/use/),  we assume it is in
the public domain. Derived data included in this package is also in the public domain. Metadata in this package ( contained in the ``metadata.csv`` file ) is
derived from metadata for the source package, and is also in the public domain. 

Programs used for data transformation (contained in the ``notebooks`` directory), are Copyright 2021 Civic Knowledge, and
are relased under the [Creative Commons Attribution-ShareAlike 4.0 International
License.](https://creativecommons.org/licenses/by-sa/4.0/)

<!-- end_license -->

