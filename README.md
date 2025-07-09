<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Thabang Moremi - Data Analyst Portfolio</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: "Cool Neutral" - A professional and clean palette using shades of slate gray, a calm blue for accents, and a light gray/white background. It's modern, easy on the eyes, and keeps the focus on the content. -->
    <!-- Application Structure Plan: A single-page, top-down narrative structure. It starts with a strong Hero section (introduction), followed by key sections: Skills, Projects, Certifications, and Contact. This linear flow is intuitive for recruiters, allowing them to scroll through a logical story of the candidate's qualifications. Navigation is handled by a sticky top bar that allows quick jumps to any section, enhancing usability. The "Projects" section is designed to be the interactive core, with a modal/detail view for each project to keep the main page uncluttered while providing depth on demand. This structure is chosen for its clarity, storytelling effectiveness, and ease of navigation for a professional portfolio. -->
    <!-- Visualization & Content Choices: 
        -   **Introduction (Hero)**: Goal: Inform/Engage. Method: Large, compelling text block. Interaction: None. Justification: Immediately establishes identity and career goal.
        -   **Skills**: Goal: Compare/Inform. Method: Horizontal Bar Chart (Chart.js). Interaction: Tooltips on hover to show proficiency context. Justification: A bar chart provides a quick, visual comparison of skill levels, which is more engaging than a simple list. Chart.js is lightweight and ideal for this.
        -   **Projects**: Goal: Organize/Explore. Method: Interactive Cards with a Modal window. Interaction: Clicking a card opens a modal with detailed project information (problem, tools, outcome) and a link to the GitHub repo. Justification: This keeps the main portfolio clean while allowing deep dives into specific work, a crucial feature for recruiters. It's a common and effective UI pattern.
        -   **Certifications**: Goal: Inform/Validate. Method: Styled content block with a prominent "Verify" button. Interaction: Button click opens the Credly URL. Justification: Makes the certification immediately visible and easily verifiable, adding credibility.
        -   **Contact**: Goal: Connect. Method: Simple list with clear icons. Interaction: Links open respective platforms (GitHub, LinkedIn, mail client). Justification: Standard, effective, and user-friendly.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8fafc;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            height: 450px;
            max-height: 500px;
        }
        @media (max-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }
        .nav-link {
            transition: color 0.3s;
        }
        .nav-link:hover {
            color: #3b82f6;
        }
        .project-card {
            transition: transform 0.3s, box-shadow 0.3s;
        }
        .project-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
        .modal-overlay {
            transition: opacity 0.3s ease-in-out;
        }
    </style>
</head>
<body class="text-slate-700">

    <!-- Header & Navigation -->
    <header class="bg-white/80 backdrop-blur-lg sticky top-0 z-50 shadow-sm">
        <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
            <a href="#" class="text-2xl font-bold text-slate-800">Thabang Moremi</a>
            <div class="hidden md:flex space-x-8">
                <a href="#skills" class="nav-link font-medium">Skills</a>
                <a href="#projects" class="nav-link font-medium">Projects</a>
                <a href="#certifications" class="nav-link font-medium">Certifications</a>
                <a href="#contact" class="nav-link font-medium">Contact</a>
            </div>
            <button id="mobile-menu-button" class="md:hidden p-2 rounded-md focus:outline-none focus:ring-2 focus:ring-slate-500">
                 <div class="w-6 h-0.5 bg-slate-800 mb-1.5"></div>
                 <div class="w-6 h-0.5 bg-slate-800 mb-1.5"></div>
                 <div class="w-6 h-0.5 bg-slate-800"></div>
            </button>
        </nav>
        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden px-6 pb-4">
            <a href="#skills" class="block py-2 nav-link">Skills</a>
            <a href="#projects" class="block py-2 nav-link">Projects</a>
            <a href="#certifications" class="block py-2 nav-link">Certifications</a>
            <a href="#contact" class="block py-2 nav-link">Contact</a>
        </div>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto px-6 py-12">

        <!-- Hero Section -->
        <section id="hero" class="text-center py-16">
            <h1 class="text-5xl md:text-6xl font-bold text-slate-800 mb-4">Aspiring Junior Data Analyst</h1>
            <p class="max-w-3xl mx-auto text-lg text-slate-600 leading-relaxed">
                Welcome to my portfolio. I am a passionate and highly motivated analyst with a solid foundation in data cleaning, analysis, visualization, and storytelling. My goal is to leverage data to uncover insights, solve real-world problems, and drive informed decision-making. I am eager to apply my skills and grow within a dynamic team.
            </p>
        </section>

        <!-- Skills Section -->
        <section id="skills" class="py-16">
            <div class="text-center mb-12">
                <h2 class="text-4xl font-bold text-slate-800">Skills & Technologies</h2>
                <p class="text-slate-600 mt-2">Here's a visual overview of my technical proficiency. I rate my confidence and experience in each tool on a scale of 1 to 10. Hover over the bars for more context.</p>
            </div>
            <div class="bg-white p-4 sm:p-8 rounded-xl shadow-lg">
                <div class="chart-container">
                    <canvas id="skillsChart"></canvas>
                </div>
            </div>
        </section>

        <!-- Projects Section -->
        <section id="projects" class="py-16">
            <div class="text-center mb-12">
                <h2 class="text-4xl font-bold text-slate-800">Projects</h2>
                 <p class="text-slate-600 mt-2">These projects showcase my ability to tackle data problems from start to finish. Click on a project to see the details.</p>
            </div>
            <div id="project-list" class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Project cards will be injected here by JavaScript -->
            </div>
        </section>

        <!-- Certifications Section -->
        <section id="certifications" class="py-16 bg-white rounded-xl shadow-lg">
             <div class="text-center mb-12">
                <h2 class="text-4xl font-bold text-slate-800">Education & Certifications</h2>
                <p class="text-slate-600 mt-2">My formal training in data analytics, validating my foundational and practical skills.</p>
            </div>
            <div class="max-w-4xl mx-auto text-center">
                <div class="p-8 border border-slate-200 rounded-lg">
                    <h3 class="text-2xl font-bold text-slate-800">Google Data Analytics Professional Certificate</h3>
                    <p class="text-blue-500 font-medium my-2">Coursera</p>
                    <p class="text-slate-600 my-4 max-w-2xl mx-auto">
                        This comprehensive 8-course program provided me with practical, hands-on experience in the entire data analysis process, from data collection and cleaning to analysis with SQL and R, visualization with Tableau, and presenting actionable insights.
                    </p>
                    <a href="https://www.credly.com/badges/d3b86007-1249-4934-92d7-708b3a567ba4/public_url" target="_blank" rel="noopener noreferrer" class="inline-block bg-blue-500 text-white font-bold py-3 px-6 rounded-lg hover:bg-blue-600 transition-colors">
                        Verify Certificate
                    </a>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="py-16">
            <div class="text-center">
                <h2 class="text-4xl font-bold text-slate-800">Contact Me</h2>
                <p class="text-slate-600 mt-2 mb-8">I'm currently seeking entry-level opportunities. Let's connect!</p>
                <div class="flex justify-center items-center space-x-8">
                     <a href="https://github.com/Thabang-m7598" target="_blank" rel="noopener noreferrer" class="text-slate-600 hover:text-blue-500 transition-colors">
                        <span class="text-4xl">🗂️</span>
                        <span class="block mt-1">GitHub</span>
                    </a>
                    <a href="https://www.linkedin.com/in/thabang-moremi" target="_blank" rel="noopener noreferrer" class="text-slate-600 hover:text-blue-500 transition-colors">
                         <span class="text-4xl">🔗</span>
                         <span class="block mt-1">LinkedIn</span>
                    </a>
                    <a href="mailto:brendanmoremi794@gmail.com" class="text-slate-600 hover:text-blue-500 transition-colors">
                         <span class="text-4xl">✉️</span>
                         <span class="block mt-1">Email</span>
                    </a>
                </div>
            </div>
        </section>

    </main>

    <!-- Project Modal -->
    <div id="project-modal" class="modal-overlay fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 hidden opacity-0 z-50">
        <div id="modal-content" class="bg-white rounded-lg shadow-2xl w-full max-w-3xl max-h-[90vh] overflow-y-auto transform scale-95 transition-transform duration-300">
            <div class="sticky top-0 bg-white p-4 border-b flex justify-between items-center">
                 <h3 id="modal-title" class="text-2xl font-bold text-slate-800"></h3>
                 <button id="modal-close" class="text-slate-500 hover:text-slate-800">&times;</button>
            </div>
            <div class="p-6">
                <div id="modal-body"></div>
                <div class="mt-6 text-center">
                    <a id="modal-link" href="#" target="_blank" rel="noopener noreferrer" class="inline-block bg-slate-700 text-white font-bold py-2 px-5 rounded-lg hover:bg-slate-800 transition-colors">
                        View on GitHub
                    </a>
                </div>
            </div>
        </div>
    </div>


    <script>
        document.addEventListener('DOMContentLoaded', function () {
            // Mobile Menu Toggle
            const mobileMenuButton = document.getElementById('mobile-menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            mobileMenuButton.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });

            // Smooth scrolling for nav links
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    if (mobileMenu.classList.contains('hidden') === false) {
                        mobileMenu.classList.add('hidden');
                    }
                    document.querySelector(this.getAttribute('href')).scrollIntoView({
                        behavior: 'smooth'
                    });
                });
            });

            // Skills Chart
            const skillsData = {
                labels: ['SQL', 'Excel', 'R (dplyr, tidyr)', 'Tableau', 'ggplot2', 'Google Sheets', 'PowerPoint'],
                datasets: [{
                    label: 'Skill Proficiency (out of 10)',
                    data: [8, 9, 7, 8, 7, 9, 8],
                    backgroundColor: 'rgba(59, 130, 246, 0.5)',
                    borderColor: 'rgba(59, 130, 246, 1)',
                    borderWidth: 1,
                    hoverBackgroundColor: 'rgba(59, 130, 246, 0.8)'
                }]
            };

            const skillsChartCtx = document.getElementById('skillsChart').getContext('2d');
            new Chart(skillsChartCtx, {
                type: 'bar',
                data: skillsData,
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        x: {
                            beginAtZero: true,
                            max: 10,
                            grid: {
                                color: '#e2e8f0'
                            },
                            ticks: {
                                color: '#475569'
                            }
                        },
                        y: {
                            grid: {
                                display: false
                            },
                            ticks: {
                                color: '#475569',
                                font: {
                                    weight: '500'
                                }
                            }
                        }
                    },
                    plugins: {
                        legend: {
                            display: false
                        },
                        tooltip: {
                            backgroundColor: '#1e293b',
                            titleFont: {
                                size: 14
                            },
                            bodyFont: {
                                size: 12
                            },
                            callbacks: {
                                label: function(context) {
                                    let label = context.dataset.label || '';
                                    if (label) {
                                        label += ': ';
                                    }
                                    if (context.parsed.x !== null) {
                                        label += context.parsed.x + ' / 10';
                                    }
                                    return label;
                                }
                            }
                        }
                    }
                }
            });

            const projectList = document.getElementById('project-list');
            const modal = document.getElementById('project-modal');
            const modalContent = document.getElementById('modal-content');
            const modalTitle = document.getElementById('modal-title');
            const modalBody = document.getElementById('modal-body');
            const modalLink = document.getElementById('modal-link');
            const modalClose = document.getElementById('modal-close');

            // Populate project cards
            projects.forEach(project => {
                const card = document.createElement('div');
                card.className = 'project-card bg-white p-6 rounded-xl shadow-md cursor-pointer';
                card.dataset.projectId = project.id;
                
                let tagsHtml = '';
                project.tags.forEach(tag => {
                    tagsHtml += `<span class="inline-block bg-blue-100 text-blue-800 text-xs font-semibold mr-2 px-2.5 py-0.5 rounded-full">${tag}</span>`;
                });

                card.innerHTML = `
                    <h3 class="text-xl font-bold text-slate-800 mb-2">${project.title}</h3>
                    <div class="mb-4">${tagsHtml}</div>
                    <p class="text-slate-600">${project.summary}</p>
                `;
                projectList.appendChild(card);
            });

            // Modal functionality
            projectList.addEventListener('click', (e) => {
                const card = e.target.closest('.project-card');
                if (card) {
                    const projectId = card.dataset.projectId;
                    const project = projects.find(p => p.id === projectId);
                    if (project) {
                        modalTitle.textContent = project.title;
                        modalBody.innerHTML = `
                            <div class="space-y-4">
                                <div>
                                    <h4 class="font-bold text-lg text-slate-700">The Problem</h4>
                                    <p class="text-slate-600">${project.problem}</p>
                                </div>
                                <div>
                                    <h4 class="font-bold text-lg text-slate-700">Tools Used</h4>
                                    <p class="text-slate-600">${project.tools}</p>
                                </div>
                                <div>
                                    <h4 class="font-bold text-lg text-slate-700">Outcome & Recommendations</h4>
                                    <p class="text-slate-600">${project.outcome}</p>
                                </div>
                            </div>
                        `;
                        modalLink.href = project.link;
                        modal.classList.remove('hidden');
                        setTimeout(() => {
                           modal.classList.remove('opacity-0');
                           modalContent.classList.remove('scale-95');
                        }, 10);
                    }
                }
            });

            const closeModal = () => {
                modal.classList.add('opacity-0');
                modalContent.classList.add('scale-95');
                setTimeout(() => modal.classList.add('hidden'), 300);
            };

            modalClose.addEventListener('click', closeModal);
            modal.addEventListener('click', (e) => {
                if (e.target === modal) {
                    closeModal();
                }
            });
        });
    </script>
</body>
</html>
