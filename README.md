# week1
semantic html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Accessible Form Example</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio</title>
    <script>
        function toggleDetails(sectionId, buttonId) {
            var details = document.getElementById(sectionId);
            var button = document.getElementById(buttonId);
    
            if (details.style.display === 'none' || details.style.display === '') {
                details.style.display = 'block';
                button.setAttribute('aria-expanded', 'true');
                details.setAttribute('aria-hidden', 'false');
            } else {
                details.style.display = 'none';
                button.setAttribute('aria-expanded', 'false');
                details.setAttribute('aria-hidden', 'true');
            }
        }
    
        function handleKeyPress(event, sectionId, buttonId) {
            if (event.key === "Enter" || event.key === " ") {
                event.preventDefault();
                toggleDetails(sectionId, buttonId);
            }
        }
    </script>
    
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
        }
        header {
            background: #bdb7e0;
            color: #ce6da1;
            padding: 1rem 0;
            text-align: center;
        }
        nav {
            margin: 1rem 0;
        }
        nav a {
            color: #ffff;
            margin: 0 1rem;
            text-decoration: none;
        }
        nav a:focus {
            outline: 2px solid #dc93bf;
            outline-offset: 2px;
        }
        section {
            padding: 2rem;
        }
        .experiences article {
            border: 1px solid #b87878;
            padding: 1rem;
            margin-bottom: 1rem;
        }
        .experiences img {
            max-width: 100%;
            height: auto;
            display: block;
            margin: 0 auto 1rem auto;
        }
        footer {
            text-align: center;
            background: #f0b9cd;
            color: #270d0d;
            padding: 1rem 0;
            margin-top: 2rem;
        }
    </style>
</head>
<body>
    
    <header role="banner">
        <h1>Welcome to My Portfolio</h1>
        <nav role="navigation">
            <a href="#about" aria-label="Navigate to About Me Section">About Me</a>
            <a href="#experiences" aria-label="Navigate to Experiences Section">Experiences</a>
            <a href="#contact" aria-label="Navigate to Contact Section">Contact</a>
        </nav>
    </header>

    <main role="main">
        <section id="about" role="region" aria-labelledby="about-heading">
            <h2 id="about-heading">About Me</h2>
            <p>Hello! I am a passionate educator with experience in teaching diverse learners and fostering engaging classroom environments. I enjoy inspiring students, simplifying complex concepts, and creating dynamic, inclusive learning experiences that encourage growth and curiosity.</p>
            
            <h3>Personal Information</h3>
            <ul>
                <li><strong>Name:</strong> Aung Suu May(예지)</li>
                <li><strong>Date of Birth:</strong> May 19th, 2002</li>
                <li><strong>Current Education:</strong> Bachelor in Computer Science, Rangsit University</li>
                <li><strong>Education:</strong> Diploma in Korean Language, Myongji University(명지대학교)</li>
            </ul>
        </section>
        

        <section id="experiences" class="experiences" role="region" aria-labelledby="experiences-heading">
            <h2 id="experiences-heading">Teaching Experiences</h2>

            <article role="article" aria-labelledby="experience1-title">
                <h3 id="experience1-title">Courses Taught</h3>
                
                <p>Engaging and interactive language courses designed to help students build communication skills, cultural understanding, and confidence in using the target language.</p>
                
                <button id="toggle-course-btn" aria-expanded="false" aria-controls="course-details" 
                        onclick="toggleCourseDetails()" onkeypress="handleKeyPress(event)" 
                        tabindex="0">
                    View Details
                </button>
                
                <div id="course-details" style="display:none; margin-top: 1rem;" aria-hidden="true">
                    <h4 tabindex="0">Language Courses Taught</h4>
                    <ul>
                        <li tabindex="0"><strong>Korean Language:</strong> Beginner to Advanced Level</li>
                        <li tabindex="0"><strong>Topik:</strong> Level 1-5</li>
                        <li tabindex="0"><strong>EPS Topik:</strong> Advanced Level</li>
                    </ul>
                </div>
            </article>
            
            <script>
                function toggleCourseDetails() {
                    var details = document.getElementById('course-details');
                    var button = document.getElementById('toggle-course-btn');
            
                    if (details.style.display === 'none') {
                        details.style.display = 'block';
                        button.setAttribute('aria-expanded', 'true');
                        details.setAttribute('aria-hidden', 'false');
                    } else {
                        details.style.display = 'none';
                        button.setAttribute('aria-expanded', 'false');
                        details.setAttribute('aria-hidden', 'true');
                    }
                }
            
                function handleKeyPress(event) {
                    if (event.key === "Enter" || event.key === " ") {
                        event.preventDefault();
                        toggleCourseDetails();
                    }
                }
            </script>
            
            
            <article role="article" aria-labelledby="experience2-title">
                <h3 id="experience2-title">Student Demographics</h3>
            
                <p>Understanding my students is key to designing effective lessons. Click below to explore more details:</p>
            
                <button id="toggle-demographics-btn" aria-expanded="false" aria-controls="demographics-details"
                        onclick="toggleDetails('demographics-details', 'toggle-demographics-btn')" 
                        onkeypress="handleKeyPress(event, 'demographics-details', 'toggle-demographics-btn')" 
                        tabindex="0">
                    View Details
                </button>
            
                <div id="demographics-details" style="display:none; margin-top: 1rem;" aria-hidden="true">
                    <h4 tabindex="0">Age Group</h4>
                    <p tabindex="0">The students I work with range from teenagers (ages 14-18) in high school to young adults (ages 18-30) in language institutes.</p>
                    
                    <h4 tabindex="0">Cultural and Linguistic Diversity</h4>
                    <p tabindex="0">I teach students from diverse linguistic and cultural backgrounds, including Spanish-speaking learners in the English course and Chinese or Arabic-speaking students in French and Spanish courses.</p>
                    
                    <h4 tabindex="0">Learning Styles</h4>
                    <p tabindex="0">Many students are visual learners, benefiting from flashcards, video materials, and infographics. Others are auditory learners who thrive in conversational activities and listening exercises. Additionally, I often support students with learning disabilities by offering extra time for assignments and using technology like text-to-speech tools.</p>
                    
                    <h4 tabindex="0">Motivation</h4>
                    <p tabindex="0">My students range from motivated language enthusiasts eager to learn and explore cultures, to those with limited exposure to language learning and needing extra support to stay engaged.</p>
                </div>
            </article>
            
            <article role="article" aria-labelledby="experience3-title">
                <h3 id="experience3-title">Teaching Methods and Strategies</h3>
            
                <p>My teaching approach is designed to engage students and enhance their language proficiency. Click below to explore the methods I use.</p>
            
                <button id="toggle-teaching-btn" aria-expanded="false" aria-controls="teaching-methods"
                        onclick="toggleDetails('teaching-methods', 'toggle-teaching-btn')" 
                        onkeypress="handleKeyPress(event, 'teaching-methods', 'toggle-teaching-btn')" 
                        tabindex="0">
                    View Details
                </button>
            
                <div id="teaching-methods" style="display:none; margin-top: 1rem;" aria-hidden="true">
                    <h4 tabindex="0">1. Communicative Language Teaching (CLT)</h4>
                    <p tabindex="0">Emphasizing real-life communication, I design activities such as role-plays, group discussions, and interactive dialogues to help students use the target language naturally and confidently.</p>
                    
                    <h4 tabindex="0">2. Task-Based Learning (TBL)</h4>
                    <p tabindex="0">Students engage in meaningful tasks—such as planning a trip, writing emails, or creating presentations—that require them to use the language authentically while developing problem-solving skills.</p>
                    
                    <h4 tabindex="0">3. Total Physical Response (TPR)</h4>
                    <p tabindex="0">For beginner learners, I incorporate movement-based activities where students physically respond to commands, reinforcing vocabulary and grammar through action and repetition.</p>
                    
                    <h4 tabindex="0">4. Flipped Classroom Approach</h4>
                    <p tabindex="0">I provide students with instructional videos, readings, or podcasts to review before class, allowing in-person lessons to focus on discussion, practice, and application of language skills.</p>
                    
                    <h4 tabindex="0">5. Technology-Enhanced Learning</h4>
                    <p tabindex="0">Using digital tools like Duolingo, Quizlet, and interactive whiteboards, I create engaging exercises that enhance vocabulary retention and listening comprehension. Online discussion forums also encourage students to practice writing and critical thinking.</p>
                    
                    <h4 tabindex="0">6. Differentiated Instruction</h4>
                    <p tabindex="0">Recognizing diverse learning styles, I offer a variety of resources—visual aids, audiobooks, conversation drills, and storytelling—to accommodate auditory, visual, and kinesthetic learners.</p>
                    
                    <h4 tabindex="0">7. Formative Assessment and Feedback</h4>
                    <p tabindex="0">I provide continuous feedback through peer reviews, self-assessments, and teacher evaluations, ensuring students track their progress and identify areas for improvement in their language learning journey.</p>
                </div>
            </article>
            
            <script>
                function toggleDetails(sectionId, buttonId) {
                    var details = document.getElementById(sectionId);
                    var button = document.getElementById(buttonId);
            
                    if (details.style.display === 'none') {
                        details.style.display = 'block';
                        button.setAttribute('aria-expanded', 'true');
                        details.setAttribute('aria-hidden', 'false');
                    } else {
                        details.style.display = 'none';
                        button.setAttribute('aria-expanded', 'false');
                        details.setAttribute('aria-hidden', 'true');
                    }
                }
            
                function handleKeyPress(event, sectionId, buttonId) {
                    if (event.key === "Enter" || event.key === " ") {
                        event.preventDefault();
                        toggleDetails(sectionId, buttonId);
                    }
                }
            </script>
            <h2>Registration Form</h2>
        
            
            <section id="Contact Information">
                <h2>Contact Information Form</h2>
                <p>If you'd like to get in touch, click below:</p>
            
                
                <button id="register-btn" onclick="toggleRegisterForm()" aria-expanded="false" aria-controls="register-form">
                    Click to Register
                </button>
            
                <!-- Hidden Registration Form -->
                <div id="register-form" style="display: none; margin-top: 1rem;" aria-hidden="true">
                    <form action="submit_registration.php" method="post">
                        <label for="name">Full Name:</label>
                        <input type="text" id="name" name="name" required><br><br>
            
                        <label for="email">Email:</label>
                        <input type="email" id="email" name="email" required><br><br>
            
                        <label for="phone_number">Phone number:</label>
                        <input type="phone_number" id="phone_number" name="phone_number" required><br><br>
            
                        <button type="submit">Register</button>
                    </form>
                </div>
            </section>
            
            <script>
                function toggleRegisterForm() {
                    var form = document.getElementById('register-form');
                    var button = document.getElementById('register-btn');
            
                    if (form.style.display === 'none' || form.style.display === '') {
                        form.style.display = 'block';
                        button.setAttribute('aria-expanded', 'true');
                        form.setAttribute('aria-hidden', 'false');
                    } else {
                        form.style.display = 'none';
                        button.setAttribute('aria-expanded', 'false');
                        form.setAttribute('aria-hidden', 'true');
                    }
                }
            </script>
            
                

        <section id="contact" role="region" aria-labelledby="contact-heading">
            <h2 id="contact-heading">Contact</h2>
            <p>If you'd like to get in touch, feel free to drop me a message at <a href="mailto:yourname@example.com" aria-label="Send an email to yourname@example.com">aeyumisan@gmail.com</a>.</p>
        </section>
    </main>

    <footer role="contentinfo">
        <p>&copy; 2025 All Rights Reserved</p>
    </footer>
</body>
</html>
