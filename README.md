<!DOCTYPE html>
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

        /* Toolbox */
        .toolbox {
            position: fixed;
            top: 50%;
            right: 20px;
            transform: translateY(-50%);
            z-index: 1000;
            background-color: rgba(0, 0, 0, 0.8);
            width: 50px;
            height: auto;
            border-radius: 10px;
            padding: 10px;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.5);
            transition: width 0.3s;
            cursor: default; /* Added cursor default */
        }

        .toolbox:hover {
            width: 200px;
        }

        .toolbox-item {
            color: white;
            margin-bottom: 10px;
            cursor: pointer;
            transition: transform 0.3s;
        }

        .toolbox-item:hover {
            transform: translateX(5px);
        }

        /* Added styles for custom cursor */
        .zoom-cursor {
            position: fixed;
            width: 100px;
            height: 100px;
            background-color: rgba(255, 255, 255, 0.5);
            border: 2px solid #000;
            border-radius: 50%;
            z-index: 9999;
            pointer-events: none; /* Prevent cursor from interfering with clicks */
            background-image: url('https://cdn4.iconfinder.com/data/icons/ionicons/512/icon-search-512.png');
            background-size: cover;
        }

        .highlight-cursor {
            position: fixed;
            width: 16px;
            height: 16px;
            background-color: yellow;
            border-radius: 50%;
            z-index: 9999;
            pointer-events: none; /* Prevent cursor from interfering with clicks */
            transform: translate(-50%, -50%);
            mix-blend-mode: multiply; /* Ensures the cursor color blends well with underlying text */
            animation: highlight 1s infinite alternate;
        }

        @keyframes highlight {
            0% {
                transform: scale(1);
            }

            100% {
                transform: scale(1.5);
            }
        }

        .draw-cursor {
            position: fixed;
            width: 16px;
            height: 16px;
            background-color: black;
            border-radius: 50%;
            z-index: 9999;
            pointer-events: none; /* Prevent cursor from interfering with clicks */
            transform: translate(-50%, -50%);
            mix-blend-mode: difference; /* Ensures the cursor color blends well with underlying content */
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
                    <li class="nav-item" data-toggle="tooltip" data-placement="bottom" title="Introduction">
                        <a class="nav-link" href="#introduction">Introduction</a>
                    </li>
                    <li class="nav-item" data-toggle="tooltip" data-placement="bottom" title="Software Tutorial">
                        <a class="nav-link" href="#software-tutorial">Software Tutorial</a>
                    </li>
                    <li class="nav-item" data-toggle="tooltip" data-placement="bottom" title="Simulation">
                        <a class="nav-link" href="#simulation">Simulation</a>
                    </li>
                    <li class="nav-item dropdown" data-toggle="tooltip" data-placement="bottom"
                        title="Data Analyses">
                        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button"
                            data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                            Data Analyses
                        </a>
                        <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                            <a class="dropdown-item"
                                href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Metabolomics_data.md">Metabolomic
                                data</a>
                            <a class="dropdown-item"
                                href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Single_cell_RNA_seq.md">Single
                                cell RNA seq data</a>
                            <a class="dropdown-item"
                                href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Spatial%20_transcriptomic.md">Spatial
                                Transcriptomic data</a>
                        </div>
                    </li>
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
            <li id="introLink" data-toggle="tooltip" data-placement="right" title="Introduction">
                <a href="#introduction">
                    <i class="fas fa-book-open"></i>
                    <span>Introduction</span>
                </a>
            </li>
            <li id="newsLink" data-toggle="tooltip" data-placement="right" title="News">
                <a href="#news">
                    <i class="fas fa-newspaper"></i>
                    <span>News</span>
                </a>
            </li>
            <li id="installationLink" data-toggle="tooltip" data-placement="right" title="Installation">
                <a href="#installation">
                    <i class="fas fa-tools"></i>
                    <span>Installation</span>
                </a>
            </li>
            <li id="applicationsLink" data-toggle="tooltip" data-placement="right" title="Applications">
                <a href="#applications">
                    <i class="fas fa-tasks"></i>
                    <span>Applications</span>
                </a>
            </li>
        </ul>
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
                <li><a href="https://www.pnas.org/doi/abs/10.1073/pnas.1220873111" style="color: blue;">Cacciatore,
                        S., Luchinat, C., & Tenori, L. (2014). Knowledge discovery by accuracy maximization. Proceedings
                        of the National Academy of Sciences, 111(14), 5117-5122.</a></li>
            </ul>
        </div>
    </section>

    <!-- Installation Section -->
    <section id="installation" class="data-section">
        <div class="container">
            <h2>Installation</h2>
            <p>
                The KODAMA is available on <a href="https://CRAN.R-project.org/package=KODAMA"
                    style="color: blue;">CRAN</a>.
            </p>
            <pre><code style="color: blue;">
library(<span style="color: black;">devtools</span>)
install_github("<span style="color: green;">tkcaccia/KODAMA</span>")
            </code></pre>
        </div>
    </section>

    <!-- Applications Section -->
    <section id="applications" class="data-section">
        <div class="container">
            <h2>Applications</h2>
            <div class="card-deck">
                <div class="card">
                    <div class="card-body">
                        <h5 class="card-title">Metabolomic data</h5>
                        <p class="card-text">Explore Metabolomic data</p>
                    </div>
                </div>
                <div class="card">
                    <div class="card-body">
                        <h5 class="card-title">Single cell RNA seq data</h5>
                        <p class="card-text">Explore Single cell RNA seq data</p>
                    </div>
                </div>
                <div class="card">
                    <div class="card-body">
                        <h5 class="card-title">Spatial Transcriptomic data</h5>
                        <p class="card-text">Explore Spatial Transcriptomic data</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Toolbox -->
    <div class="toolbox">
        <div class="toolbox-item" data-toggle="tooltip" data-placement="left" title="Zoom"
            onclick="toggleZoom()">
            <i class="fas fa-search"></i>
        </div>
        <div class="toolbox-item" data-toggle="tooltip" data-placement="left" title="Highlight"
            onclick="toggleHighlight()">
            <i class="fas fa-highlighter"></i>
        </div>
        <div class="toolbox-item" data-toggle="tooltip" data-placement="left" title="Draw"
            onclick="toggleDrawing()">
            <i class="fas fa-pen"></i>
        </div>
    </div>

<!-- Custom Cursors -->
<div id="zoomCursor" class="zoom-cursor"></div>
<div id="highlightCursor" class="highlight-cursor"></div>
<div id="drawCursor" class="draw-cursor"></div>

<!-- Custom Script -->
<script>
    // Toggle Zoom Function
    function toggleZoom() {
        // Change cursor to zoom icon
        document.body.style.cursor = 'url("zoom.cur"), auto';
        // Implement zoom functionality here
        // For example: document.addEventListener('mousemove', zoomFunction);
    }

    // Toggle Highlight Function
    function toggleHighlight() {
        // Change cursor to highlighter icon
        document.body.style.cursor = 'url("highlight.cur"), auto';
        // Implement highlight functionality here
        // For example: document.addEventListener('mousedown', startHighlight);
        // For example: document.addEventListener('mouseup', endHighlight);
    }

    // Toggle Drawing Function
    function toggleDrawing() {
        // Change cursor to pencil icon
        document.body.style.cursor = 'url("pencil.cur"), auto';
        // Implement drawing functionality here
        // For example: document.addEventListener('mousedown', startDrawing);
        // For example: document.addEventListener('mousemove', draw);
        // For example: document.addEventListener('mouseup', endDrawing);
    }

    // Track mouse movements for custom cursors
    document.addEventListener('mousemove', function (e) {
        const zoomCursor = document.getElementById('zoomCursor');
        const highlightCursor = document.getElementById('highlightCursor');
        const drawCursor = document.getElementById('drawCursor');
        
        // Position the custom cursors
        zoomCursor.style.left = `${e.clientX}px`;
        zoomCursor.style.top = `${e.clientY}px`;
        highlightCursor.style.left = `${e.clientX}px`;
        highlightCursor.style.top = `${e.clientY}px`;
        drawCursor.style.left = `${e.clientX}px`;
        drawCursor.style.top = `${e.clientY}px`;
    });
</script>


</body>

</html>
