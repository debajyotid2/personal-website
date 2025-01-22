---
date: '2025-01-19T11:37:47-05:00'
draft: false
title: 'Projects'
hidemeta: true
ShowShareButtons: true
---

## Past

### [Sea Turtle Conservation Using Feature Matching Algorithms](https://www.fruitpunch.ai/blog/tracking-turtles-how-ai-helps-conservationists-to-re-identify-sea-turtles)

Jan 2024 – Apr 2024

{{< collapse summary="🔍 Detailed Overview" >}}

Collaborating with [Sea Turtle Conservation Bonaire (STCB)](https://www.bonaireturtles.org/wp/), we developed an AI-driven application to identify individual sea turtles from photographs, enhancing conservation efforts by understanding their migratory patterns. As a member of the feature extraction and matching team in the "AI for Turtles" project, our primary goal was to develop a system capable of accurately identifying individual sea turtles from photographs. After evaluating various methods including [SIFT](https://home.cis.rit.edu/~cnspci/references/dip/feature_extraction/lowe1999.pdf) and [LoFTR](https://openaccess.thecvf.com/content/CVPR2021/papers/Sun_LoFTR_Detector-Free_Local_Feature_Matching_With_Transformers_CVPR_2021_paper.pdf), we selected [LightGlue](https://openaccess.thecvf.com/content/ICCV2023/papers/Lindenberger_LightGlue_Local_Feature_Matching_at_Light_Speed_ICCV_2023_paper.pdf) for feature extraction due to its superior performance, achieving a 92% matching accuracy and 86% accuracy in detecting novel individuals. LightGlue utilizes the SIFT algorithm to identify key points in images, which are then matched to determine the top five similar turtles in the database. We introduced the use of the Wasserstein score to assess the distribution of confidence scores for keypoint pairs, aiding in the identification process. This approach significantly enhanced the efficiency and accuracy of re-identifying sea turtles, providing conservationists with a powerful tool to monitor and protect these endangered species.

**Key technologies**: PyTorch, Kornia, Docker, HuggingFace Transformers, Computer Vision, Deep Learning.
{{< /collapse >}}
\
{{< project-badge "computer vision" "Computer Vision" >}}
{{< project-badge "deep learning" "Deep Learning" >}}
{{< project-badge "representation learning" "Representation Learning" >}}

### [Toxic Industrial Smoke Detection from Camera Feed](https://www.frissewind.nu/articles/ai)

Jul 2023 – Feb 2024

{{< collapse summary="🔍 Detailed Overview" >}}

As developers on the AI monitoring project of [Fruitpunch AI](https://www.fruitpunch.ai/) for emissions from a steel plant, we collaborated with [FrisseWind.nu](https://www.frissewind.nu/) and [Greenpeace Netherlands](https://www.greenpeace.org/nl/) to create an AI system that automatically detects harmful emissions from the steel plant. We integrated this system with existing webcams and the [SpotdeGifwolk.nl](https://spotdegifwolk.nl/) platform, enabling real-time monitoring of the factories. Our deep learning model successfully identified multiple prohibited emissions which were reported to the authorities for enforcement. This innovation significantly increased the efficiency of monitoring efforts, allowing for more comprehensive oversight of environmental impact of the steel plant.

**Key technologies**: PyTorch, OpenCV, TensorRT SDK, TorchServe, TorchScript, HuggingFace Transformers, Computer Vision, Deep Learning.
{{< /collapse >}}
\
{{< project-badge "computer vision" "Computer Vision" >}}
{{< project-badge "deep learning" "Deep Learning" >}}
{{< project-badge "video classification" "Video Classification" >}}
{{< project-badge "tensorrt" "TensorRT" >}}

### [Multivariate Linear Regression Using Stochastic Gradient Descent](https://github.com/debajyotid2/gradient_descent)

Jul 2023 – Aug 2023

{{< collapse summary="🔍 Detailed Overview" >}}

This project demonstrates multivariate linear regression using stochastic gradient descent, implemented in both C and Python. The C version leverages the OpenBLAS library for efficient matrix and vector operations, while the Python version utilizes NumPy for similar functionalities. Both implementations include scripts for building and running the code, as well as unit tests to ensure correctness. This project serves as an educational tool for understanding and applying gradient descent algorithms in linear regression models.

**Key technologies**: NumPy, BLAS, Optimization, Linear Algebra, HPC, Machine Learning.
{{< /collapse >}}
\
{{< project-badge "linear algebra" "Linear Algebra" >}}
{{< project-badge "optimization" "Optimization" >}}
{{< project-badge "hpc" "HPC" >}}

### [Uncertainty Analysis of Alzheimer’s Disease Cell-Free mRNA Assay Classifier](https://media.licdn.com/dms/document/media/v2/D562DAQEahK4YdCa1gw/profile-treasury-document-pdf-analyzed/profile-treasury-document-pdf-analyzed/0/1732575334006?e=1738195200&v=beta&t=qaGLTUFGYh6Jrsnb9XKJVuxTJYuk4j7PZ16xqvc19U0)

Jan 2023 – May 2023

{{< collapse summary="🔍 Detailed Overview" >}}

Leading the student team as part of [The Data Mine](https://datamine.purdue.edu/) in this project, we focused on modeling the measurement uncertainty of a high-dimensional RNA-Seq classifier for Alzheimer’s Disease using Monte Carlo simulations per FDA guidance. The classifier, built with penalized logistic regression on 965 genes, was analyzed to assess variations under different levels of relative standard deviation in transcript counts. My team designed modular and reproducible software to efficiently simulate and document assay variations, leveraging the [Anvil supercomputer](https://www.rcac.purdue.edu/anvil) for large-scale computation. We found that differential classification primarily occurred near the binary classification threshold, with significant robustness to simulated variations due to the classifier’s high dimensionality. Our work highlights the importance of rigorous measurement uncertainty modeling in advancing precision medicine and improving diagnostic reproducibility.

**Key technologies**: NumPy, Uncertainty Analysis, Monte Carlo simulations, HPC.
{{< /collapse >}}
\
{{< project-badge "uncertainty analysis" "Uncertainty Analysis" >}}
{{< project-badge "monte carlo simulations" "Monte Carlo Simulations" >}}
{{< project-badge "bioinformatics" "Bioinformatics" >}}
{{< project-badge "hpc" "HPC" >}}

### [Activation Energy Prediction from Reaction Data](https://github.com/debajyotid2/activation_energy_prediction)

Jan 2023 – May 2023

{{< collapse summary="🔍 Detailed Overview" >}}

This project focuses on developing machine learning models to predict the activation energies of chemical reactions, leveraging advanced computational methods and chemical datasets composed of [SMILES](https://daylight.com/dayhtml/doc/theory/theory.smiles.html) strings. Created as part of my master’s capstone project under the guidance of [Prof. Brett Savoie](https://engineering.nd.edu/faculty/brett-savoie/), the project integrates domain knowledge with data-driven techniques to address challenges in reaction kinetics. By analyzing key molecular features, the models aim to improve the accuracy and efficiency of predicting activation energy, facilitating advancements in catalyst design and reaction optimization. The repository includes scripts for preprocessing data, training models, and evaluating predictions, providing a comprehensive toolkit for future research in this domain.

**Key technologies**: Cheminformatics, RDKit, Scikit-learn, PyTorch.
{{< /collapse >}}
\
{{< project-badge "cheminformatics" "Cheminformatics" >}}
{{< project-badge "machine learning" "Machine Learning" >}}
{{< project-badge "regression" "Regression" >}}

---

## Current

### [Cryptopals Cryptography Challenges](https://github.com/debajyotid2/cryptopals)

{{< collapse summary="🔍 Detailed Overview" >}}

The [Cryptopals](https://cryptopals.com/) project is a collection of cryptography challenges aimed at exposing vulnerabilities in modern cryptographic algorithms, which I am solving using Rust. This endeavor has significantly deepened my understanding of cryptographic principles and enhanced my proficiency in Rust. Currently, I have completed Sets 1 through 6, covering topics from basic encoding to RSA and DSA, and I continue to work on the remaining sets. The project is organized with each set as its own crate, facilitating modular development and testing.

**Key technologies**: Rust, Cryptography.

{{< /collapse >}}
\
{{< project-badge "cryptography" "Cryptography" >}}

### [A Matrix Library in C](https://github.com/debajyotid2/matlibr)

{{< collapse summary="🔍 Detailed Overview" >}}

The `matlibr` project is a barebones implementation of a 2D matrix datatype in C, designed to perform basic matrix operations such as addition, subtraction, and multiplication, with acceleration provided by [BLAS](https://www.netlib.org/blas/) libraries.  Developing this library has enhanced my understanding of matrix computations and the integration of BLAS for performance optimization in C. Currently, the project supports double precision and integer data types, matrix-scalar operations, matrix-vector operations, gather operations along rows or columns, and computation of L1 and L2 norms.  I continue to work on expanding its functionality and improving its efficiency. 

**Key technologies**: BLAS, Linear Algebra, C.

{{< /collapse >}}
\
{{< project-badge "linear algebra" "Linear Algebra" >}}
{{< project-badge "hpc" "HPC" >}}

### [A Thread Pool in C](https://github.com/debajyotid2/yatpool)

{{< collapse summary="🔍 Detailed Overview" >}}

The `yatpool` project is a thread pool implementation in pure C, utilizing [POSIX threads](https://www.man7.org/linux/man-pages/man7/pthreads.7.html) to manage and execute multiple tasks concurrently.  Developing this project has enhanced my understanding of multithreading and synchronization mechanisms in C, particularly in creating efficient and reusable thread management systems. Currently, the project features a simple API for initializing the thread pool, submitting tasks, and managing their execution.  I continue to work on expanding its functionality and improving its efficiency. 

**Key technologies**: POSIX threads, C.

{{< /collapse >}}
\
{{< project-badge "hpc" "HPC" >}}
{{< project-badge "parallel computing" "Parallel computing" >}}

### [Advent of Code](https://github.com/debajyotid2/adventofcode)

{{< collapse summary="🔍 Detailed Overview" >}}

This project involves my ongoing attempt at solving the [Advent of Code](https://adventofcode.com/) challenges.

**Key technologies**: Python.

{{< /collapse >}}
\
{{< project-badge "programming challenge" "Programming Challenge" >}}
