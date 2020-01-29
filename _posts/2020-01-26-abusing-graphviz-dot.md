---
layout: post
title: Abusing Graphviz DOT for Beautiful Network Visualizations
subtitle: "Creating eye-catching hierarchies by abusing the label feature."
description: How to make hierarchical graphs in Graphviz.
permalink: abusing-graphviz-dot
image: /img/sentiventlogo.jpg
tags: [graphviz, dot, struct, label, data Visualization, taxonomy, type, hierarchy]
published: false
---

When writing data science reports

Problem: Create 
Candidate solutions:
- NetworkX + Plot.ly/Matplotlib: Does not support clustering; 
- NetworkX + GraphvizDOT: First prototype in Graphviz DOT, then review data; manual entry in vanilly graphviz is not desirable for many datapoints, however writing a custom generator is also a lot of work.
- GraphvizDOT: Prototype for feasability
Solution: Use struct and label in GraphvizDOT

# struct and label

'''DOT
graph EventTaxonomies {

    size="8.267,11.7!"

    rankdir = LR;
    graph [fontsize=10 fontname="CMU Serif Extra"];
    node [shape=record fontsize=9 fontname="CMU Serif"];

    subgraph cluster_0 {
        rankdir = TB;
        node [style=filled];
        "LegalIssue1" [label="LegalIssue"]
        "MergerAcquisition" "Price" "SecurityIncrease" "ProductLaunch" "ProductRelease";
        label = "Container A";
        color=blue;
    }

    subgraph cluster_1 {
        node [style=filled];
        "NIGGASIFFY" "Item 4" "LegalIssue2" [label="LegalIssue"];
        label = "Container B";
        color=blue;
    }

    subgraph cluster_2 {
        node [style=filled];
        "Item 5" "Item 6";
        label = "Container C";
        color=blue;
    }

    subgraph cluster_3 {
        // node [style=filled];
        teststruct [label="MergerAcquisition|<price1>Price|SecurityIncrease|ProductLaunch|{ProductRelease|{Release|<CR>CancelRecall|PIP}}"];
        label = "ProjectNAME (F.N. AuthorLastname, F.2. AuthorLastname2)";
        color=blue;
    }
    
    subgraph cluster_4 {
        // node [style=filled];
        teststruct2 [label="MergerAcquisition|{<price2>Price|{Increase|Decrease|Stable}}|SecurityIncrease|ProductLaunch|{ProductService|{Release|<CR>CancelRecall|PIP}}"];
        label = "ProjectNAME (F.N. AuthorLastname, F.2. AuthorLastname2)";
        color=blue;
    }

    // Renders fine
    "LegalIssue1" -- "LegalIssue2" [style=dotted];
    "LegalIssue2" -- "Item 6" [style=dashed];
    "LegalIssue1" -- "Item 6" [style=dotted];
    teststruct:CR -- "Item 6";
    price1 -- price2 [style=dashed];
}
'''