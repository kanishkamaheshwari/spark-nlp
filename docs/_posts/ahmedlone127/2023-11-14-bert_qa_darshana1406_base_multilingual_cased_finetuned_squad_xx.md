---
layout: model
title: Multilingual BertForQuestionAnswering Base Cased model (from darshana1406)
author: John Snow Labs
name: bert_qa_darshana1406_base_multilingual_cased_finetuned_squad
date: 2023-11-14
tags: [xx, open_source, bert, question_answering, onnx]
task: Question Answering
language: xx
edition: Spark NLP 5.2.0
spark_version: 3.0
supported: true
engine: onnx
annotator: BertForQuestionAnswering
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained BertForQuestionAnswering model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `bert-base-multilingual-cased-finetuned-squad` is a Multilingual model originally trained by `darshana1406`.

## Predicted Entities



{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/bert_qa_darshana1406_base_multilingual_cased_finetuned_squad_xx_5.2.0_3.0_1700001977877.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/bert_qa_darshana1406_base_multilingual_cased_finetuned_squad_xx_5.2.0_3.0_1700001977877.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python
Document_Assembler = MultiDocumentAssembler()\
     .setInputCols(["question", "context"])\
     .setOutputCols(["document_question", "document_context"])

Question_Answering = BertForQuestionAnswering.pretrained("bert_qa_darshana1406_base_multilingual_cased_finetuned_squad","xx")\
     .setInputCols(["document_question", "document_context"])\
     .setOutputCol("answer")\
     .setCaseSensitive(True)
    
pipeline = Pipeline(stages=[Document_Assembler, Question_Answering])

data = spark.createDataFrame([["What's my name?","My name is Clara and I live in Berkeley."]]).toDF("question", "context")

result = pipeline.fit(data).transform(data)
```
```scala
val Document_Assembler = new MultiDocumentAssembler()
     .setInputCols(Array("question", "context"))
     .setOutputCols(Array("document_question", "document_context"))

val Question_Answering = BertForQuestionAnswering.pretrained("bert_qa_darshana1406_base_multilingual_cased_finetuned_squad","xx")
     .setInputCols(Array("document_question", "document_context"))
     .setOutputCol("answer")
     .setCaseSensitive(true)
    
val pipeline = new Pipeline().setStages(Array(Document_Assembler, Question_Answering))

val data = Seq("What's my name?","My name is Clara and I live in Berkeley.").toDS.toDF("question", "context")

val result = pipeline.fit(data).transform(data)
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|bert_qa_darshana1406_base_multilingual_cased_finetuned_squad|
|Compatibility:|Spark NLP 5.2.0+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[document_question, document_context]|
|Output Labels:|[answer]|
|Language:|xx|
|Size:|665.0 MB|
|Case sensitive:|true|
|Max sentence length:|512|

## References

References

- https://huggingface.co/darshana1406/bert-base-multilingual-cased-finetuned-squad