<KODAMA >
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <style>
        /* Navbar Styles */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            background-color: #333;
            border-radius: 0;
            transition: transform 0.3s;
        }

        .navbar:hover {
            transform: scale(1.1);
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.5);
        }

        .navbar-nav .nav-link {
            color: white;
            transition: color 0.3s, background-color 0.3s;
        }

        .navbar-nav .nav-link:hover {
            color: #FFA500;
            background-color: rgba(255, 165, 0, 0.1);
        }

        /* Body padding to compensate for fixed navbar */
        body {
            padding-top: 56px;
            margin-left: 0;
            background-color: #f8f9fa;
            font-family: Arial, sans-serif;
        }

        /* Sidebar Styles */
        #sidebar {
            position: fixed;
            top: 50%;
            left: 0;
            transform: translateY(-50%);
            z-index: 1000;
            background-color: #343a40;
            width: 70px;
            height: auto;
            overflow: hidden;
            transition: width 0.3s;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.2);
        }

        #sidebar:hover {
            width: 200px;
        }

        #sidebar ul {
            list-style-type: none;
            padding: 0;
            margin: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100%;
        }

        #sidebar ul li {
            width: 200px;
            padding: 15px;
            color: white;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
            display: flex;
            align-items: center;
            justify-content: flex-start;
        }

        #sidebar ul li:hover {
            background-color: #adb5bd;
            transform: translateX(10px);
        }

        #sidebar ul li a {
            text-decoration: none;
            color: inherit;
        }

        #sidebar ul li i {
            margin-right: 10px;
        }

        .sidebar-item-content {
            display: none;
            padding: 10px;
            color: white;
            background-color: #343a40;
            position: absolute;
            left: 200px;
            top: 0;
            z-index: 1000;
            width: 200px;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.2);
            border-top-right-radius: 10px;
            border-bottom-right-radius: 10px;
            animation: fadeIn 0.3s;
        }

        #sidebar ul li:hover .sidebar-item-content {
            display: block;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }

            to {
                opacity: 1;
            }
        }

        .sidebar-item-title {
            font-weight: bold;
            margin-bottom: 5px;
        }

        /* Custom Styles for Data Sections */
        .data-section {
            margin-top: 20px;
            padding: 20px;
            border-radius: 10px;
            background-color: #fff;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
            animation: fadeInUp 1s ease;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .data-section h2 {
            color: #007bff;
            margin-bottom: 20px;
        }

        .data-section p {
            color: #343a40;
            margin-bottom: 20px;
        }

        /* Card Styles */
        .card {
            border: none;
            border-radius: 10px;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .card:hover {
            transform: scale(1.05);
            box-shadow: 0px 0px 30px rgba(0, 0, 0, 0.2);
        }

        .card-title {
            color: #007bff;
            font-weight: bold;
        }

        .card-text {
            color: #343a40;
        }

        /* Toolbox Styles */
        .toolbox {
            position: fixed;
            top: 50%;
            right: 20px;
            transform: translateY(-50%);
            z-index: 1000;
            background-color: rgba(0, 0, 0, 0.5);
            border-radius: 10px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-around;
            padding: 10px;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.5);
            transition: background-color 0.3s, transform 0.3s;
        }

        .toolbox:hover {
            background-color: rgba(0, 0, 0, 0.8);
        }

        .toolbox-icon {
            color: white;
            font-size: 24px;
            cursor: pointer;
            transition: transform 0.3s;
            position: relative;
        }

        .toolbox-icon:hover {
            transform: scale(1.1);
        }

        .tooltip {
            visibility: hidden;
            width: 120px;
            background-color: rgba(0, 0, 0, 0.8);
            color: #fff;
            text-align: center;
            border-radius: 6px;
            padding: 5px 0;
            position: absolute;
            z-index: 1;
            bottom: 125%;
            left: 50%;
            margin-left: -60px;
            opacity: 0;
            transition: opacity 0.3s;
        }

        .toolbox-icon:hover .tooltip {
            visibility: visible;
            opacity: 1;
        }

        /* Highlighting Style */
        .highlighted {
            background-color: yellow !important;
        }

        /* Drawing Style */
        .drawing-canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 999;
            pointer-events: none;
        }
    </style>
</head>

<body>

    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
            <a class="navbar-brand" href="#">
                KODAMA
            </a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
                aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">
                    <!-- Ajoutez vos liens de navigation ici -->
                </ul>
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <a class="nav-link" href="https://github.com/tkcaccia/KODAMA">
                            <span class="fab fa-github"></span>
                            Source code
                        </a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- Sidebar -->
    <div id="sidebar">
        <ul>
            <!-- Ajoutez vos éléments de la barre latérale ici -->
        </ul>
    </div>

    <!-- Toolbox -->
    <div class="toolbox">
        <div class="toolbox-icon" onclick="toggleZoom()">
            <i class="fas fa-search"></i>
            <span class="tooltip">Loupe (Zoom)</span>
        </div>
        <div class="toolbox-icon" onclick="toggleHighlight()">
            <i class="fas fa-highlighter"></i>
            <span class="tooltip">Surligner</span>
        </div>
        <div class="toolbox-icon" onclick="toggleDrawing()">
            <i class="fas fa-pen"></i>
            <span class="tooltip">Crayon (Dessiner)</span>
        </div>
    </div>

    <!-- Introduction Section -->
    <section id="introduction" class="data-section">
        <div class="container">
            <h2>Introduction</h2>
            <p>
                # KODAMA An unsupervised and semi-supervised learning algorithm to perform feature extraction from
                noisy and high-dimensional data
            </p>
        </div>
    </section>

    <!-- News Section -->
    <section id="news" class="data-section">
        <div class="container">
            <h2>News</h2>
            <p>
                KODAMA facilitates identification of patterns representing underlying groups on all samples in a data
                set. This is an improved version of KODAMA algorithm for spatially-aware dimensionality reduction. A
                landmarks procedure has been implemented to adapt the algorithm to the analysis of data set with more
                than 10,000 entries.
            </p>
            <p>
                The KODAMA package has been integrated with t-SNE and UMAP to convert the KODAMA's dissimilarity
                matrix in a low dimensional space.
            </p>
            <ul>
                <li><a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9887019/"
                        style="color: blue;">Zinga, M. M.,
                        Abdel-Shafy, E., Melak, T., Vignoli, A., Piazza, S., Zerbini, L. F., ... & Cacciatore, S.
                        (2022). KODAMA exploratory analysis in metabolic phenotyping. Frontiers in Molecular Biosciences,
                        9.</a></li>
                <li><a href="https://academic.oup.com/bioinformatics/article/33/4/621/2667156?login=false"
                        style="color: blue;">Cacciatore, S., Tenori, L., Luchinat, C., Bennett, P. R., & MacIntyre, D.
                        A. (2017). KODAMA: an R package for knowledge discovery and data mining. Bioinformatics,
                        33(4), 621-623.</a></li>
                <li><a href="https://www.pnas.org/doi/abs/10.1073/pnas.1423999112"
                        style="color: blue;">Cacciatore, S., Zerbini, L. F., Piazza, S., Menendez, P., Luchinat, C.,
                        & Tenori, L. (2015). KODAMA: a workflow for distance-based molecule activity
                        prediction.</a></li>
            </ul>
        </div>
    </section>

    <!-- Installation Section -->
    <section id="installation" class="data-section">
        <div class="container">
            <h2>Installation</h2>
            <p>
                To install KODAMA, run the following commands in your R environment:
            </p>
            <pre><code class="r">install.packages("devtools")
devtools::install_github("tkcaccia/KODAMA")</code></pre>
        </div>
    </section>

    <!-- Applications Section -->
    <section id="applications" class="data-section">
        <div class="container">
            <h2>Applications</h2>
            <p>
                KODAMA has been applied to various areas of research including:
            </p>
            <ul>
                <li>Metabolomics</li>
                <li>Single cell RNA sequencing</li>
                <li>Spatial transcriptomics</li>
            </ul>
            <p>
                For detailed applications, refer to the respective documentation available on the GitHub repository.
            </p>
        </div>
    </section>

    <!-- Bootstrap JS and Font Awesome -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js"
        integrity="sha384-D/EoTKB8smFbAxNhH6vGnqz87ls2xanFgpF/nFziItVHZCKsaP+FKlV7zVZE3Cs3"
        crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"
        integrity="sha384-JMkP+udwY6qL4v4hVaH3ai6f3oT63KStwBxVubuXGfbsp7f7s+sFPrV92S9KFkFf"
        crossorigin="anonymous"></script>
    <script src="https://kit.fontawesome.com/a076d05399.js"></script>

    <!-- Custom Script -->
    <script>
        // Fonction pour basculer le zoom
        function toggleZoom() {
            alert("Basculer le zoom !");
            // Votre logique pour le zoom ici
        }

        // Fonction pour basculer le surlignage
        function toggleHighlight() {
            alert("Basculer le surlignage !");
            // Votre logique pour le surlignage ici
        }

        // Fonction pour basculer le dessin
        function toggleDrawing() {
            alert("Basculer le dessin !");
            // Votre logique pour le dessin ici
        }
    </script>
</body>

</html>
