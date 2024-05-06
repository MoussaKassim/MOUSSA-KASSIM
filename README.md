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
            border-radius: 0; /* Rounded rectangle */
        }
        .navbar-nav .nav-link {
            color: white;
            transition: color 0.3s, background-color 0.3s; /* Transition for glowing effect */
        }
        .navbar-nav .nav-link:hover {
            color: #FFA500; /* Modern orangish color */
            background-color: rgba(255, 165, 0, 0.1); /* Orange background */
        }
        .navbar-brand {
            color: white;
            font-size: 24px;
        }
        /* Body padding to compensate for fixed navbar */
        body {
            padding-top: 56px; /* Height of the navbar */
            margin-left: 0; /* Adjusted to accommodate the sidebar */
            background-color: #f8f9fa; /* Background color for body */
            font-family: Arial, sans-serif; /* Font family for better readability */
        }
        /* Sidebar Styles */
        #sidebar {
            position: fixed;
            top: 50%;
            left: 0;
            transform: translateY(-50%);
            z-index: 1000;
            background-color: #343a40; /* Darker sidebar background */
            width: 70px;
            height: auto;
            overflow: hidden;
            transition: width 0.3s;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.2);
        }
        #sidebar:hover {
            width: 150px;
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
            width: 150px;
            padding: 10px;
            color: white;
            cursor: pointer;
            transition: background-color 0.3s;
            display: flex;
            align-items: center;
            justify-content: flex-start;
        }
        #sidebar ul li:hover {
            background-color: #adb5bd; /* Lighter background color on hover */
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
            left: 150px;
            top: 0;
            z-index: 1000;
            width: 200px;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.2);
            border-top-right-radius: 10px;
            border-bottom-right-radius: 10px;
        }
        #sidebar ul li:hover .sidebar-item-content {
            display: block;
            animation: fadeIn 0.3s;
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
    </style>
</head>

<body>

    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
            <a class="navbar-brand" href="#">KODAMA</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
                aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">
                    <li class="nav-item">
                        <a class="nav-link" href="#introduction">Introduction</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#software-tutorial">Software Tutorial</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#simulation">Simulation</a>
                    </li>
                    <li class="nav-item dropdown">
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
            <li>
                <a href="#introduction">
                    <i class="fas fa-book-open"></i>
                    <div class="sidebar-item-content">
                        <span class="sidebar-item-title">Introduction</span>
                        <span>Learn about KODAMA</span>
                    </div>
                </a>
            </li>
            <li>
                <a href="#news">
                    <i class="fas fa-newspaper"></i>
                    <div class="sidebar-item-content">
                        <span class="sidebar-item-title">News</span>
                        <span>Get the latest updates</span>
                    </div>
                </a>
            </li>
            <li>
                <a href="#installation">
                    <i class="fas fa-tools"></i>
                    <div class="sidebar-item-content">
                        <span class="sidebar-item-title">Installation</span>
                        <span>Get started with KODAMA</span>
                    </div>
                </a>
            </li>
            <li>
                <a href="#applications">
                    <i class="fas fa-tasks"></i>
                    <div class="sidebar-item-content">
                        <span class="sidebar-item-title">Applications</span>
                        <span>Explore different uses</span>
                    </div>
                </a>
            </li>
        </ul>
    </div>

    <!-- Introduction Section -->
    <section id="introduction">
        <div class="container">
            <h1>Introduction</h1>
            <p>
                # KODAMA An unsupervised and semi-supervised learning algorithm to perform feature extraction from
                noisy and high-dimensional data
            </p>
        </div>
    </section>

    <!-- News Section -->
    <section id="news">
        <div class="container">
            <h2>News</h2>
            <p>
                <span>KODAMA facilitates identification of patterns representing underlying groups on all samples in a
                    data set.
                    This is an improved version of KODAMA algorithm for spatially-aware dimensionality reduction. A
                    landmarks procedure has been implemented to adapt the algorithm to the analysis of data set with
                    more than 10,000 entries.</span>
            </p>
            <p>
                <span>The KODAMA package has been integrated with t-SNE and UMAP to convert the KODAMA's dissimilarity
                    matrix in a low dimensional space.</span>
            </p>
            <p>
                <ul>
                    <li><a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9887019/"
                            style="color: blue; text-decoration: underline;">Zinga, M. M., Abdel-Shafy, E., Melak,
                            T., Vignoli, A., Piazza, S., Zerbini, L. F., ... & Cacciatore, S. (2022). KODAMA
                            exploratory analysis in metabolic phenotyping. Frontiers in Molecular Biosciences,
                            9.</a></li>
                    <li><a href="https://academic.oup.com/bioinformatics/article/33/4/621/2667156?login=false"
                            style="color: blue; text-decoration: underline;">Cacciatore, S., Tenori, L., Luchinat,
                            C., Bennett, P. R., & MacIntyre, D. A. (2017). KODAMA: an R package for knowledge
                            discovery and data mining. Bioinformatics, 33(4), 621-623.</a></li>
                    <li><a href="https://www.pnas.org/doi/abs/10.1073/pnas.1220873111"
                            style="color: blue; text-decoration: underline;">Cacciatore, S., Luchinat, C., &
                            Tenori, L. (2014). Knowledge discovery by accuracy maximization. Proceedings of the
                            National Academy of Sciences, 111(14), 5117-5122.</a></li>
                </ul>
            </p>
        </div>
    </section>

    <!-- Installation Section -->
    <section id="installation">
        <div class="container">
            <h2>Installation</h2>
            <p>
                The KODAMA is available on <a href="https://CRAN.R-project.org/package=KODAMA">CRAN</a>.
            </p>
            <pre><code style="color: blue;">
library(<span style="color: black;">devtools</span>)
install_github("<span style="color: green;">tkcaccia/KODAMA</span>")
        </code></pre>
        </div>
    </section>

    <!-- Applications Section -->
    <section id="applications">
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

    <!-- Bootstrap Scripts -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.3/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

    <!-- Font Awesome Script -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/js/all.min.js"></script>

    <!-- JavaScript for Smooth Scrolling and Active Navigation -->
    <script>
        // Smooth scrolling for sidebar links
        document.getElementById('sidebar').addEventListener('mouseenter', function () {
            this.style.width = '150px';
        });
        document.getElementById('sidebar').addEventListener('mouseleave', function () {
            this.style.width = '70px';
        });
    </script>

</body>

</html>
