<!-- Source: https://learn.microsoft.com/en-us/graph/education-rubric-overview -->
<!-- Sitemap-Last-Modified: 2025-08-06 -->

# Education rubric overview

Rubrics are an effective and widely used way of grading assignments, and the education API in Microsoft Graph supports them.

A grading rubric is a matrix of *qualities*, *levels*, and *criteria*, as follows:

|  | Level | Level |
| :--- | :--- | :--- |
| Quality | Criterion | Criterion |
| Quality | Criterion | Criterion |

An example of a grading rubric might be:

|  | Good | Poor |
| :--- | :--- | :--- |
| Argument | The essay's argument is persuasive. | The essay's argument doesn't make sense. |
| Spelling and grammar | The essay uses proper spelling and grammar with few or no errors. | The essay has numerous errors in spelling and/or grammar. |

Grading using a rubric involves selecting one *level* for each *quality* in the rubric.

A rubric *might* have points associated with each level, and a weight associated with each quality. If present, weights must add up to 100.

|  | Good \(2 points\) | Poor \(1 point\) |
| :--- | :--- | :--- |
| Argument \(weight 50\) | The essay's argument is persuasive. | The essay's argument doesn't make sense. |
| Spelling and grammar \(weight 50\) | The essay uses proper spelling and grammar with few or no errors. | The essay has numerous errors in spelling and/or grammar. |

## API reference

To begin using rubrics, start with the [educationRubric resource in Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric) and associated methods.
