# mdb-concepts-adapter

The api spec for all the functionality contained here can be found at : https://app.swaggerhub.com/apis/srimanta.maji/CCOVA/v1
The individual elements present here directly correspond to the api category found at the above swagger link.

## mdb-concept-curation

Contains the functionality grouped under "Concept Curation".

### Properties:

1. **apiToken**: The api authentication token.
2. **apiUrlBase**: The base path of the api.

### Methods

#### getConceptDetailsAsync(conceptId: string)
 Returns a Promise of the current concept definition from /domains/{conceptId}.

#### getConceptFacetsAsync(conceptId: string, facetFilters: object, existingConceptDetails: object)
Returns a Promise of concept facets the details of which are provided below.

| Parameter | Description |
| -- | -- |
| conceptId | concept id to fetch facets from. |
| facetFilters | filters to pivot on. <br> Has the structure : {patterns: ['pattern1'], synonyms: ['synonym'], relatedDomains: ['relatedDomain'], exampleColumns: ['exampleColumn'], exampleValues: ['exampleValue']} |
| existingConceptDetails<br>(optional) | existing concept details object which can be used to base the facet extraction on. Further usage defined below. |

**Method execution steps**
1. In case the "existingConceptDetails" parameter is not supplied, it fetches that using the concept id.
2. In the current concept definition(fetched above), if there are no exampleColumns present, it goes for bootstrapping the concept curation by hitting the **/columns** endpoint, otherwise it fetches facets from the **/clusters** endpoint. In either case, it applies the filters provided.
3. The facets fetched are then updated in two steps: 
- Update assessments of facets from the concept details in step 1.
- Merge the facets and their counterparts obtained in step 1.

#### getConceptsAsync(userId: string, paging: object)
Returns a Promise of the concepts listing  as per the requested page of results.

| Parameter | Description |
| -- | -- |
| userId | User Identifier |
| paging | Pagination value of the form: {limit: number, offset: number} |

#### curateConceptAsync(concept: object)

Asynchronously updates the concept definition with the provided concept details.

| Parameter | Description |
| -- | -- |
| concept | Contains the updated assessment per facet as : {synonyms: [], patterns: [], exampleColumns: [], exampleValues: [], relatedConcepts: []} with each of these collections of the format: {id: string, label: string, assessment: string} |