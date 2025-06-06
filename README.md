

# Flow-Bench

**[Paper](./flow_bench_arxiv.pdf) | [Dataset](#Dataset) | [Approach](#approach) | [Videos](#videos) | [How to Cite](#how-to-cite) | [Contributors](#contributors)**

### Dataset

The dataset is in support of our approach to utilize LLMs to translate natural language into an intermediate representation with Python syntax that facilitates final conversion into widely adopted business process definition languages.

The approach and the methodology that was used to create and validate the dataset can be found in the arxiv [paper](https://arxiv.org/pdf/2505.11646) 

The dataset consists of 101 incremental build test cases targeted at supporting and evaluating approaches and research in natural language-driven business process automation.

To ensure compact and clear representations of prior context and expected workflows, FLOW-BENCH adopts a constrained subset of Python syntax. This subset includes assignment statements, conditional statements (if-statements), loops (for and while), and function calls.

The `conditional_ootb.yaml` file contains the 101 tests. An example test is shown below:

```
  - _metadata:
      tags:
        - "97"
        - conditional_update
        - conditional_update_replace
      uid: 97
    input:
      utterance: |-
        Instead of retrieving all the issues just create a new issue in each repo
      prior_sequence:
        - |-
          repositories = GitHub_Repository__3_0_0__retrievewithwhere_Repository()
          for repo in repositories:
            new_issue = GitHub_Issue__3_0_0__retrievewithwhere_Issue()
      prior_context: []
      bpmn:
        $ref: "context/uid_97_context.bpmn"
    expected_output:
      sequence:
        - |-
          repositories = GitHub_Repository__3_0_0__retrievewithwhere_Repository()
          for repo in repositories:
            updated_issue = GitHub_Issue__3_0_0__create_Issue()
      bpmn:
        $ref: "output/uid_97_output.bpmn"
```

The example contains `metadata` along with `tags` that outline whether the test is `conditional`, or `linear` as well as if its `update`, `delete` or implicitly `creation`.
The `prior_sequence` contains pythonic syntax representation of the previously created BPMN. `bpmn` points to the corresponding BPMN representations available in the `context` folder.
The `expected_output` contains the groud truth pythonic syntax representation as well as a reference to the `bpmn` representation which can be found in the `output` folder.

The `ootb_catalog.json` file contains the unique identified `id` as well as the `description` of the API. An example is shown below

```
{
    "id": "bambooHR_benefits__2_0_0__retrievewithwhere_benefits",
    "description": "Retrieve all the benefit deduction types"
}
```

### Approach

For details on the approach to generate flows and the evaluation results on the tests suite refer to Sections 3 and 4 of the arxiv [paper](https://arxiv.org/pdf/2505.11646), respectively.

### Videos

Here are some videos showcasing our approach for multiple use cases.

https://github.com/user-attachments/assets/f0c21b29-b6cd-43c4-ae5b-44fd89faf945

https://github.com/user-attachments/assets/f74b33d4-246f-407d-a5d6-5b22efb434df

https://github.com/user-attachments/assets/e2c6b1b1-3c08-481f-a4e1-0876870d555c




### How to Cite

```
@misc{duesterwald2025flowbench,
      title={FLOW-BENCH: Towards Conversational Generation of Enterprise Workflows}, 
      author={Evelyn Duesterwald and Siyu Huo and Vatche Isahagian and K. R. Jayaram and Ritesh Kumar and Vinod Muthusamy and Punleuk Oum and Debashish Saha and Gegi Thomas and Praveen Venkateswaran},
      year={2025},
      url={https://arxiv.org/abs/2505.11646}, 
}
```

## Contributors
In alphabetical order
- Evelyn Duesterwald
- Siyu Huo
- Vatche Isahagian
- K.R. Jayaram
- Ritesh Kumar
- Vinod Muthusamy
- Punleuk Oum
- Debashish Saha
- Gegi Thomas
- Praveen Venkateswaran
