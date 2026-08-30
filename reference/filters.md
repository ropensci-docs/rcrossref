# Get filter details and names.

Get filter details and names.

## Usage

``` r
filter_names()

filter_details(x = NULL)
```

## Arguments

- x:

  (character) Optional filter name. If not given, all filters returned.

## Details

Note that all filter names in this package have periods and dashes
replaced with underscores as they both cause problems in an R console.

## Examples

``` r
filter_names()
#>  [1] "award_funder"              "award_number"             
#>  [3] "content_domain"            "from_accepted_date"       
#>  [5] "from_online_pub_date"      "from_posted_date"         
#>  [7] "from_print_pub_date"       "has_assertion"            
#>  [9] "has_authenticated_orcid"   "has_crossmark_restriction"
#> [11] "has_relation"              "location"                 
#> [13] "relation_object"           "relation_object_type"     
#> [15] "relation_type"             "until_accepted_date"      
#> [17] "until_online_pub_date"     "until_posted_date"        
#> [19] "until_print_pub_date"      "has_funder"               
#> [21] "funder"                    "prefix"                   
#> [23] "member"                    "from_index_date"          
#> [25] "until_index_date"          "from_deposit_date"        
#> [27] "until_deposit_date"        "from_update_date"         
#> [29] "until_update_date"         "from_pub_date"            
#> [31] "until_pub_date"            "has_license"              
#> [33] "license_url"               "license_version"          
#> [35] "license_delay"             "has_full_text"            
#> [37] "full_text_version"         "full_text_type"           
#> [39] "full_text_application"     "has_references"           
#> [41] "reference_visibility"      "has_archive"              
#> [43] "archive"                   "has_orcid"                
#> [45] "orcid"                     "issn"                     
#> [47] "isbn"                      "type"                     
#> [49] "directory"                 "doi"                      
#> [51] "updates"                   "is_update"                
#> [53] "has_update_policy"         "container_title"          
#> [55] "category_name"             "type_name"                
#> [57] "from_created_date"         "until_created_date"       
#> [59] "has_affiliation"           "assertion_group"          
#> [61] "assertion"                 "article_number"           
#> [63] "alternative_id"            "has_clinical_trial_number"
#> [65] "has_abstract"              "has_content_domain"       
#> [67] "has_domain_restriction"   
filter_details()
#> $has_funder
#> $has_funder$possible_values
#> [1] NA
#> 
#> $has_funder$description
#> [1] "metadata which includes one or more funder entry"
#> 
#> 
#> $funder
#> $funder$possible_values
#> [1] "{funder_id}"
#> 
#> $funder$description
#> [1] "metadata which include the {funder_id} in FundRef data"
#> 
#> 
#> $prefix
#> $prefix$possible_values
#> [1] "{owner_prefix}"
#> 
#> $prefix$description
#> [1] "metadata belonging to a DOI owner prefix {owner_prefix} (e.g. '10.1016' )"
#> 
#> 
#> $member
#> $member$possible_values
#> [1] "{member_id}"
#> 
#> $member$description
#> [1] "metadata belonging to a CrossRef member"
#> 
#> 
#> $from_index_date
#> $from_index_date$possible_values
#> [1] "{date}"
#> 
#> $from_index_date$description
#> [1] "metadata indexed since (inclusive) {date}"
#> 
#> 
#> $until_index_date
#> $until_index_date$possible_values
#> [1] "{date}"
#> 
#> $until_index_date$description
#> [1] "metadata indexed before (inclusive) {date}"
#> 
#> 
#> $from_deposit_date
#> $from_deposit_date$possible_values
#> [1] "{date}"
#> 
#> $from_deposit_date$description
#> [1] "metadata last (re)deposited since (inclusive) {date}"
#> 
#> 
#> $until_deposit_date
#> $until_deposit_date$possible_values
#> [1] "{date}"
#> 
#> $until_deposit_date$description
#> [1] "metadata last (re)deposited before (inclusive) {date}"
#> 
#> 
#> $from_update_date
#> $from_update_date$possible_values
#> [1] "{date}"
#> 
#> $from_update_date$description
#> [1] "Metadata updated since (inclusive) {date} Currently the same as 'from_deposit_date'"
#> 
#> 
#> $until_update_date
#> $until_update_date$possible_values
#> [1] "{date}"
#> 
#> $until_update_date$description
#> [1] "Metadata updated before (inclusive) {date} Currently the same as 'until_deposit_date'"
#> 
#> 
#> $from_created_date
#> $from_created_date$possible_values
#> [1] "{date}"
#> 
#> $from_created_date$description
#> [1] "metadata first deposited since (inclusive) {date}"
#> 
#> 
#> $until_created_date
#> $until_created_date$possible_values
#> [1] "{date}"
#> 
#> $until_created_date$description
#> [1] "metadata first deposited before (inclusive) {date}"
#> 
#> 
#> $from_pub_date
#> $from_pub_date$possible_values
#> [1] "{date}"
#> 
#> $from_pub_date$description
#> [1] "metadata where published date is since (inclusive) {date}"
#> 
#> 
#> $until_pub_date
#> $until_pub_date$possible_values
#> [1] "{date}"
#> 
#> $until_pub_date$description
#> [1] "metadata where published date is before (inclusive)  {date}"
#> 
#> 
#> $has_license
#> $has_license$possible_values
#> [1] NA
#> 
#> $has_license$description
#> [1] "metadata that includes any '<license_ref>' elements"
#> 
#> 
#> $license_url
#> $license_url$possible_values
#> [1] "{url}"
#> 
#> $license_url$description
#> [1] "metadata where '<license_ref>' value equals {url}"
#> 
#> 
#> $license_version
#> $license_version$possible_values
#> [1] "{string}"
#> 
#> $license_version$description
#> [1] "metadata where the '<license_ref>''s 'applies_to' attribute  is '{string}'"
#> 
#> 
#> $license_delay
#> $license_delay$possible_values
#> [1] "{integer}"
#> 
#> $license_delay$description
#> [1] "metadata where difference between publication date and the '<license_ref>''s 'start_date' attribute is <= '{integer}' (in days"
#> 
#> 
#> $has_full_text
#> $has_full_text$possible_values
#> [1] NA
#> 
#> $has_full_text$description
#> [1] "metadata that includes any full text '<resource>' elements_"
#> 
#> 
#> $full_text_version
#> $full_text_version$possible_values
#> [1] "{string}"
#> 
#> $full_text_version$description
#> [1] "metadata where '<resource>' element's 'content_version' attribute is '{string}'"
#> 
#> 
#> $full_text_type
#> $full_text_type$possible_values
#> [1] "{mime_type}"
#> 
#> $full_text_type$description
#> [1] "metadata where '<resource>' element's 'content_type' attribute is '{mime_type}' (e.g. 'application/pdf')"
#> 
#> 
#> $full_text_application
#> $full_text_application$possible_values
#> [1] "{string}"
#> 
#> $full_text_application$description
#> [1] "metadata where <resource> link has one of the following intended applications: text-mining, similarity-checking or unspecified"
#> 
#> 
#> $has_references
#> $has_references$possible_values
#> [1] NA
#> 
#> $has_references$description
#> [1] "metadata for works that have a list of references"
#> 
#> 
#> $reference_visibility
#> $reference_visibility$possible_values
#> [1] "open, limited, closed"
#> 
#> $reference_visibility$description
#> [1] "metadata for works where references are either open, limited (to Metadata Plus subscribers) or closed"
#> 
#> 
#> $has_archive
#> $has_archive$possible_values
#> [1] NA
#> 
#> $has_archive$description
#> [1] "metadata which include name of archive partner"
#> 
#> 
#> $archive
#> $archive$possible_values
#> [1] "{string}"
#> 
#> $archive$description
#> [1] "metadata which where value of archive partner is '{string}'"
#> 
#> 
#> $has_orcid
#> $has_orcid$possible_values
#> [1] NA
#> 
#> $has_orcid$description
#> [1] "metadata which includes one or more ORCIDs"
#> 
#> 
#> $orcid
#> $orcid$possible_values
#> [1] "{orcid}"
#> 
#> $orcid$description
#> [1] "metadata where '<orcid>' element's value = '{orcid}'"
#> 
#> 
#> $issn
#> $issn$possible_values
#> [1] "{issn}"
#> 
#> $issn$description
#> [1] "metadata where record has an ISSN = '{issn}' Format is 'xxxx_xxxx'."
#> 
#> 
#> $isbn
#> $isbn$possible_values
#> [1] "{isbn}"
#> 
#> $isbn$description
#> [1] "metadata where record has an ISBN"
#> 
#> 
#> $type
#> $type$possible_values
#> [1] "{type}"
#> 
#> $type$description
#> [1] "metadata records whose type = '{type}' Type must be an ID value from the list of types returned by the '/types' resource"
#> 
#> 
#> $directory
#> $directory$possible_values
#> [1] "{directory}"
#> 
#> $directory$description
#> [1] "metadata records whose article or serial are mentioned in the given '{directory}'. Currently the only supported value is 'doaj'"
#> 
#> 
#> $doi
#> $doi$possible_values
#> [1] "{doi}"
#> 
#> $doi$description
#> [1] "metadata describing the DOI '{doi}'"
#> 
#> 
#> $updates
#> $updates$possible_values
#> [1] "{doi}"
#> 
#> $updates$description
#> [1] "metadata for records that represent editorial updates to the DOI '{doi}'"
#> 
#> 
#> $is_update
#> $is_update$possible_values
#> [1] NA
#> 
#> $is_update$description
#> [1] "metadata for records that represent editorial updates"
#> 
#> 
#> $has_update_policy
#> $has_update_policy$possible_values
#> [1] NA
#> 
#> $has_update_policy$description
#> [1] "metadata for records that include a link to an editorial update policy"
#> 
#> 
#> $container_title
#> $container_title$possible_values
#> [1] NA
#> 
#> $container_title$description
#> [1] "metadata for records with a publication title exactly with an exact match"
#> 
#> 
#> $category_name
#> $category_name$possible_values
#> [1] NA
#> 
#> $category_name$description
#> [1] "metadata for records with an exact matching category label"
#> 
#> 
#> $type_name
#> $type_name$possible_values
#> [1] NA
#> 
#> $type_name$description
#> [1] "metadata for records with an exacty matching type label"
#> 
#> 
#> $award_number
#> $award_number$possible_values
#> [1] "{award_number}"
#> 
#> $award_number$description
#> [1] "metadata for records with a matching award nunber_ Optionally combine with 'award_funder'"
#> 
#> 
#> $award_funder
#> $award_funder$possible_values
#> [1] "{funder DOI or id}"
#> 
#> $award_funder$description
#> [1] "metadata for records with an ffun with matching funder. Optionally combine with 'award_number'"
#> 
#> 
#> $assertion_group
#> $assertion_group$possible_values
#> [1] NA
#> 
#> $assertion_group$description
#> [1] "metadata for records with an assertion in a particular group"
#> 
#> 
#> $assertion
#> $assertion$possible_values
#> [1] NA
#> 
#> $assertion$description
#> [1] "metadata for records with a particular named assertion"
#> 
#> 
#> $has_affiliation
#> $has_affiliation$possible_values
#> [1] NA
#> 
#> $has_affiliation$description
#> [1] "metadata for records that have any affiliation information"
#> 
#> 
#> $article_number
#> $article_number$possible_values
#> [1] NA
#> 
#> $article_number$description
#> [1] "metadata for records with a given article number"
#> 
#> 
#> $alternative_id
#> $alternative_id$possible_values
#> [1] NA
#> 
#> $alternative_id$description
#> [1] "metadata for records with the given alternative ID, which may be a publisher_specific ID, or any other identifier a publisher may have provided"
#> 
#> 
#> $has_clinical_trial_number
#> $has_clinical_trial_number$possible_values
#> [1] NA
#> 
#> $has_clinical_trial_number$description
#> [1] "metadata for records which include a clinical trial number"
#> 
#> 
#> $has_abstract
#> $has_abstract$possible_values
#> [1] NA
#> 
#> $has_abstract$description
#> [1] "metadata for records which include an abstract"
#> 
#> 
#> $content_domain
#> $content_domain$possible_values
#> [1] NA
#> 
#> $content_domain$description
#> [1] "metadata where the publisher records a particular domain name as the location Crossmark content will appear"
#> 
#> 
#> $has_content_domain
#> $has_content_domain$possible_values
#> [1] NA
#> 
#> $has_content_domain$description
#> [1] "metadata where the publisher records a domain name location for Crossmark content"
#> 
#> 
#> $has_domain_restriction
#> $has_domain_restriction$possible_values
#> [1] NA
#> 
#> $has_domain_restriction$description
#> [1] "metadata where the publisher restricts Crossmark usage to content domains"
#> 
#> 
#> $from_accepted_date
#> $from_accepted_date$possible_values
#> [1] "{date}"
#> 
#> $from_accepted_date$description
#> [1] "metadata where accepted date is since (inclusive) {date}"
#> 
#> 
#> $from_online_pub_date
#> $from_online_pub_date$possible_values
#> [1] "{date}"
#> 
#> $from_online_pub_date$description
#> [1] "metadata where online published date is since (inclusive) {date}"
#> 
#> 
#> $from_posted_date
#> $from_posted_date$possible_values
#> [1] "{date}"
#> 
#> $from_posted_date$description
#> [1] "metadata where posted date is since (inclusive) {date}"
#> 
#> 
#> $from_print_pub_date
#> $from_print_pub_date$possible_values
#> [1] "{date}"
#> 
#> $from_print_pub_date$description
#> [1] "metadata where print published date is since (inclusive) {date}"
#> 
#> 
#> $has_assertion
#> $has_assertion$possible_values
#> [1] NA
#> 
#> $has_assertion$description
#> [1] "metadata for records with any assertions"
#> 
#> 
#> $has_authenticated_orcid
#> $has_authenticated_orcid$possible_values
#> [1] NA
#> 
#> $has_authenticated_orcid$description
#> [1] "metadata which includes one or more ORCIDs where the depositing publisher claims to have witness the ORCID owner authenticate with ORCID"
#> 
#> 
#> $has_crossmark_restriction
#> $has_crossmark_restriction$possible_values
#> [1] NA
#> 
#> $has_crossmark_restriction$description
#> [1] "metadata where the publisher restricts Crossmark usage to content domains"
#> 
#> 
#> $has_relation
#> $has_relation$possible_values
#> [1] NA
#> 
#> $has_relation$description
#> [1] "metadata for records that either assert or are the object of a relation"
#> 
#> 
#> $location
#> $location$possible_values
#> [1] "{country_name}"
#> 
#> $location$description
#> [1] "funder records where location = {country name}. Only works on /funders route"
#> 
#> 
#> $relation_object
#> $relation_object$possible_values
#> [1] NA
#> 
#> $relation_object$description
#> [1] "Relations where the object identifier matches the identifier provided"
#> 
#> 
#> $relation_object_type
#> $relation_object_type$possible_values
#> [1] NA
#> 
#> $relation_object_type$description
#> [1] "One of the identifier types from the Crossref relations schema (e.g. doi, issn)"
#> 
#> 
#> $relation_type
#> $relation_type$possible_values
#> [1] NA
#> 
#> $relation_type$description
#> [1] "One of the relation types from the Crossref relations schema (e.g. is-referenced-by, is-parent-of, is-preprint-of)"
#> 
#> 
#> $until_accepted_date
#> $until_accepted_date$possible_values
#> [1] "{date}"
#> 
#> $until_accepted_date$description
#> [1] "metadata where accepted date is before (inclusive) {date}"
#> 
#> 
#> $until_online_pub_date
#> $until_online_pub_date$possible_values
#> [1] "{date}"
#> 
#> $until_online_pub_date$description
#> [1] "metadata where online published date is before (inclusive) {date}"
#> 
#> 
#> $until_posted_date
#> $until_posted_date$possible_values
#> [1] "{date}"
#> 
#> $until_posted_date$description
#> [1] "metadata where posted date is before (inclusive) {date}"
#> 
#> 
#> $until_print_pub_date
#> $until_print_pub_date$possible_values
#> [1] "{date}"
#> 
#> $until_print_pub_date$description
#> [1] "metadata where print published date is before (inclusive) {date}"
#> 
#> 
filter_details()$has_authenticated_orcid
#> $possible_values
#> [1] NA
#> 
#> $description
#> [1] "metadata which includes one or more ORCIDs where the depositing publisher claims to have witness the ORCID owner authenticate with ORCID"
#> 
filter_details()$has_authenticated_orcid$possible_values
#> [1] NA
filter_details()$has_authenticated_orcid$description
#> [1] "metadata which includes one or more ORCIDs where the depositing publisher claims to have witness the ORCID owner authenticate with ORCID"
filter_details("issn")
#> $issn
#> $issn$possible_values
#> [1] "{issn}"
#> 
#> $issn$description
#> [1] "metadata where record has an ISSN = '{issn}' Format is 'xxxx_xxxx'."
#> 
#> 
filter_details("iss")
#> $issn
#> $issn$possible_values
#> [1] "{issn}"
#> 
#> $issn$description
#> [1] "metadata where record has an ISSN = '{issn}' Format is 'xxxx_xxxx'."
#> 
#> 
filter_details(c("issn", "alternative_id"))
#> $issn
#> $issn$possible_values
#> [1] "{issn}"
#> 
#> $issn$description
#> [1] "metadata where record has an ISSN = '{issn}' Format is 'xxxx_xxxx'."
#> 
#> 
#> $alternative_id
#> $alternative_id$possible_values
#> [1] NA
#> 
#> $alternative_id$description
#> [1] "metadata for records with the given alternative ID, which may be a publisher_specific ID, or any other identifier a publisher may have provided"
#> 
#> 
```
