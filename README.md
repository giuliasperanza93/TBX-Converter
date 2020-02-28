**README**

In this repository we provide a tool for converting CSV Linguistic Resources into TBX format. 

The tool has been developed by the [UNIOR NLP Research Group](https://sites.google.com/view/unior-nlp-research-group)
Research group for Computational Linguistics and Automatic Processing of Natural Language of the L'Orientale University of Naples.
[uniornlp@gmail.com](mailto:uniornlp@gmail.com)

The tool is released under **CC license**.

To cite this work, please use:
@inproceedings{speranza2019from,
  title={From Linguistic Resources to Ontology-Aware Terminologies:Minding the Representation Gap},
  author={Speranza, Giulia and di Buono, Maria Pia and Monti, Johanna and Sangati, Federico},
  booktitle={International Conference on Language Resources and Evaluation. LREC2020},
  year={2020}
}

The converter takes as input a **CSV file** and gives as output a **TBX file**, the standard **TermBase eXchange** format for terminology management and sharing. The converter also supports the integration of ontology references.

The CSV should contain **9 fields** separated by 8 semicolons (;) per line.

**Term*** is mandatory and must contain the term (which could be a single word or a multiword expression (MWE), e.g., *column krater, antefixes, etc.* 

**POS tag***, is mandatory and must contain the Part of Speech tag of the entry, e.g., ```N, P, A,``` etc.

**Internal POS tags** can contain the POS of MWE’s single components, e.g., ```NN``` etc.

**Grammatical info** should contain the gender and number of the term, in the format ```ns-+```

**Variants** can host all orthographic variants of a term, e.g., *column krater,column-krater*

**Synonyms** should contain the synonyms for the selected term. If more than one Synonym is available they can be listed separated by comma, as for Variants.

**Definition** is the field dedicated to a brief explication of the term like a dictionary gloss, e.g., *Kraters with columnlike handles extending from the shoulders to the rim. The feet are echinus shaped. This vessel type was especially popular in black-figure.*

**Hypernyms** can contain hierarchically higher and more general lexical entries comprising the term  e.g., *architectural elements.*

**Ontology class** reference can host the term’s corresponding ontology class in a reference domain ontology such as CIDOC CRM Ontology for Cultural Heritage domain e.g., ```E22_Man-Made_Object```

*Mandatory fields. 
If some of the optional fields are missing, the separator has to be inserted to preserve the number of expected fields.


**Example of CSV input file**

```
column krater;N;NN;ns-+;column crater,column-krater;;Kraters with columnlike handles extending from the shoulders to the rim. The feet are echinus shaped. This vessel type was especially popular in black-figure.;vessel and containers,furnishings and equipment;E22_Man-Made_Object	
antefix;N;;ns-+;antefixae;Ornaments at the ridge or eaves of a roof, in classical architecture and derivatives, that close or conceal the open end of a row of cover tiles.;architectural elements;E22_Man-Made_Object
```

**Example of TBX output file**

```
<text>
    <body>
      <termEntry id="AR_1">
        <descripGrp>
          <descrip type="subjectField">Archaeology</descrip>
          <descrip type="definition">Kraters with columnlike handles extending from the shoulders to the rim. The feet are echinus shaped. This vessel type was especially popular in black-figure.</descrip>
          <xref type="URI"target="http://www.cidoc-crm.org/cidoc-crm">CIDOC CRM Ontology</xref>
        </descripGrp>
      </termEntry>
      <langSet xml:lang="en">
        <ntig>
          <termGrp>
            <term>column krater</term>
            <termNote type="termType">fullForm</termNote>
            <termNote type="partOfSpeech">noun</termNote>
            <termNote type="grammaticalGender">neuter</termNote>
            <termNote type="grammaticalNumber">singular</termNote>
            <xref type="URI"target="http://www.cidoc-crm.org/cidoc-crm/E22_Man-Made_Object">CIDOC CRM Class</xref>
            <termCompList type="lemma">
              <termCompGrp>
                <termComp>column</termComp>
                <termNote type="partOfSpeech">noun</termNote>
              </termCompGrp>
              <termCompGrp>
                <termComp>krater</termComp>
                <termNote type="partOfSpeech">noun</termNote>
              </termCompGrp>
            </termCompList>
            <termNote type="variant01">column crater</termNote>
            <termNote type="variant02">column-krater</termNote>
            <termNote type="hypernyms01">vessel and containers</termNote>
            <termNote type="hypernyms02">furnishings and equipment</termNote>
          </termGrp>
        </ntig>
      </langSet>
      <termEntry id="AR_2">
        <descripGrp>
          <descrip type="subjectField">Archaeology</descrip>
          <descrip type="definition">Ornaments at the ridge or eaves of a roof, in classical architecture and derivatives, that close or conceal the open end of a row of cover tiles.</descrip>
          <xref type="URI" 
           target="http://www.cidoc-crm.org/cidoc-crm">CIDOC CRM Ontology</xref>
        </descripGrp>
      </termEntry>
      <langSet xml:lang="en">
        <tig>
          <term>antefix</term>
          <termNote type="termType">fullForm</termNote>
          <termNote type="partOfSpeech">noun</termNote>
          <termNote type="grammaticalGender">neuter</termNote>
          <termNote type="grammaticalNumber">singular</termNote>
          <xref type="URI"target="http://www.cidoc-crm.org/cidoc-crm/E22_Man-Made_Object"> CIDOC CRM Class</xref>
          <termNote type="variant01">antefixae</termNote>
          <termNote type="hypernyms01">architectural elements</termNote>
        </tig>
      </langSet>
    </body>
  </text>
```

This tool is available on Telegram as a ChatBot under the name CSV2TBX (https://t.me/CSV2TBX_bot).



