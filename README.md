<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@picocss/pico@1/css/pico.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/slick-carousel/1.8.1/slick.min.css" />
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/slick-carousel/1.8.1/slick-theme.min.css" />
    <style>
        body {
            background-color: #f9f9f9;
            font-family: Arial, sans-serif;
        }
        h2, h3 {
            color: #333;
        }
        p {
            color: #555;
            line-height: 1.6;
        }
        .image-container {
            width: 100%;
            height: auto;
            margin: 1rem 0;
        }
        .subscribe-form input,
        .subscribe-form button {
            margin-top: 0.3rem;
            border-radius: 20rem;
            line-height: 27.5px;
            padding: 0.3rem;
        }
        .subscribe-form input::placeholder,
        .popup-form input::placeholder,
        .popup-form select::placeholder {
            font-size: 14px;
        }
        .author-bio img {
            border-radius: 50%;
            margin-right: 1rem;
        }
        .related-posts {
            display: flex;
            flex-direction: column;
            width: 260px;
            margin-left: 20px;
            padding-top: 100px;
        }
        .related-posts h3 {
            margin-bottom: 10px;
            text-align: left;
        }
        .related-posts .card {
            width: 100%;
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 10px;
            background-color: #fff;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            text-align: center;
            margin-bottom: 10px;
        }
        .related-posts .card img {
            width: 100%;
            height: 100px;
            object-fit: cover;
            border-radius: 8px;
        }
        .related-posts .card a {
            font-size: 14px;
            color: #6D1B49;
            text-decoration: none;
            display: block;
            margin-top: 10px;
        }
        .related-posts .card a:hover {
            text-decoration: underline;
        }
        .related-posts .card .card-details {
            font-size: 12px;
            color: #888;
            margin-top: 5px;
        }
        .related-posts .card .author {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: 10px;
        }
        .related-posts .card .author img {
            border-radius: 50%;
            width: 30px;
            height: 30px;
            margin-right: 10px;
        }
        .social-icons {
            border: 1px solid #ddd;
            padding: 20px;
            border-radius: 20rem;
            background-color: #6D1B49;
            color: #fff;
            text-align: center;
            margin-top: 0.3rem;
        }
        .social-icons h3 {
            margin: 0 0 10px;
            color: #fff;
        }
        .social-icons a {
            margin: 0 5px;
            display: inline-block;
            background-color: #fff;
            padding: 10px;
            border-radius: 8px;
        }
        .social-icons a img {
            width: 20px;
            height: 20px;
        }
        .accordion {
            border: 1px solid #ccc;
            border-radius: 8px;
            overflow: hidden;
            margin-bottom: 1rem;
        }
        .accordion h3 {
            cursor: pointer;
            padding: 1rem;
            background-color: #6D1B49;
            color: #fff;
            margin: 0;
            font-size: 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .accordion h3::after {
            content: '\25BC';
            font-size: 14px;
            color: #fff;
        }
        .accordion h3.active::after {
            content: '\25B2';
        }
        .accordion p {
            padding: 1rem;
            display: none;
            margin: 0;
            font-size: 14px;
        }
        .popup-form {
            display: none;
            position: fixed;
            bottom: 0;
            right: 0;
            background-color: #fff;
            border: 1px solid #ccc;
            padding: 1rem;
            width: 300px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            z-index: 1000;
            border-radius: 8px;
        }
        .popup-form h2 {
            font-size: 20px;
            margin-bottom: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .popup-form h2 span {
            cursor: pointer;
            font-size: 14px;
            color: #6D1B49;
        }
        .popup-form form {
            display: flex;
            flex-direction: column;
        }
        .popup-form input, .popup-form select, .popup-form button {
            margin-bottom: 0.5rem;
            border-radius: 8px;
            padding: 0.5rem;
            border: 1px solid #ddd;
            font-size: 14px;
        }
        .popup-form button {
            background-color: #6D1B49;
            color: #fff;
            border: none;
            cursor: pointer;
        }
        .popup-form button:hover {
            background-color: #4c1333;
        }
        .fixed-header {
            position: fixed;
            width: 100%;
            background-color: #fff;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            z-index: 100;
        }
        .main-content {
            padding-top: 80px;
        }
        .main-content-area {
            flex: 1;
        }
        .content-wrapper {
            display: flex;
        }
        .progress-bar {
            width: 100%;
            background-color: #f3f3f3;
            border-radius: 8px;
            overflow: hidden;
            margin: 20px 0;
        }
        .progress-bar-inner {
            height: 20px;
            width: 70%;
            background-color: #6D1B49;
            border-radius: 8px 0 0 8px;
            text-align: center;
            color: white;
        }
        .statistics, .infographics {
            margin: 20px 0;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        .footer {
            background-color: #f7f7f7;
            padding: 20px 0;
            text-align: center;
            margin-top: 40px;
            border-top: 1px solid #ddd;
        }
        .footer small {
            color: #555;
            font-size: 14px;
        }
        .footer a {
            color: #6D1B49;
            text-decoration: none;
        }
        .footer a:hover {
            text-decoration: underline;
        }
        .slick-prev, .slick-next {
            display: none !important;
        }
    </style>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/slick-carousel/1.8.1/slick.min.js"></script>
    <script>
        document.addEventListener('scroll', function() {
            var popup = document.querySelector('.popup-form');
            if (!popup.classList.contains('visible')) {
                popup.classList.add('visible');
                popup.style.display = 'block';
            }
        });

        $(document).ready(function(){
            $('.carousel').slick({
                infinite: true,
                slidesToShow: 1,
                slidesToScroll: 1,
                dots: true,
                arrows: false,
                autoplay: true,
                autoplaySpeed: 3000
            });

            $('.accordion h3').on('click', function(){
                $(this).next('p').slideToggle();
                $(this).toggleClass('active');
            });

            $('.popup-form h2 span').on('click', function(){
                $('.popup-form').toggleClass('visible');
                $('.popup-form').toggle();
            });
        });
    </script>
    <title>Crowdfunding Blog Post</title>
</head>
<body>
    <main class="container main-content">
        <div class="content-wrapper">
            <div class="main-content-area">
                <div class="grid">
                    <section>
                        <hgroup>
                            <h2 style="font-size: 32px; text-align: center; margin-top: 20px;">How Crowdfunding is Transforming Lives</h2>
                        </hgroup>
                        <div class="carousel">
                            <div><img src="https://via.placeholder.com/1200x300" alt="Community Gathering" class="image-container" /></div>
                            <div><img src="https://via.placeholder.com/1200x300" alt="Fundraising Event" class="image-container" /></div>
                        </div>
                        <p style="font-style: italic; font-size: 18px; text-align: center;">
                            Crowdfunding has become a powerful tool for individuals and communities to raise funds for various causes. In this article, we explore how crowdfunding is making a significant impact.
                        </p>
                        <h3 style="font-size: 24px;">The Rise of Crowdfunding</h3>
                        <p>
                            Crowdfunding platforms have seen exponential growth in recent years. These platforms provide a space where people can come together to support various initiatives, ranging from personal projects to community-based campaigns. The ease of setting up a campaign and the ability to reach a wide audience are among the factors contributing to this growth.
                        </p>
                        <p>
                            With the advent of the internet and social media, crowdfunding has become more accessible than ever. Anyone with an idea or a cause can start a campaign and share it with their network. This democratization of fundraising has opened doors for many who would otherwise have struggled to secure traditional funding.
                        </p>
                        <div class="statistics">
                            <h3 style="font-size: 24px;">Crowdfunding Statistics</h3>
                            <div class="progress-bar">
                                <div class="progress-bar-inner">70%</div>
                            </div>
                            <p>Over 70% of crowdfunding campaigns reach their target within the first 30 days.</p>
                            <div class="progress-bar">
                                <div class="progress-bar-inner" style="width: 80%;">80%</div>
                            </div>
                            <p>80% of campaigns that reach 20% of their goal within the first week are successful.</p>
                        </div>
                        <div class="infographics">
                            <h3 style="font-size: 24px;">Infographics</h3>
                            <img src="https://via.placeholder.com/800x400" alt="Infographic">
                        </div>
                        <h3 style="font-size: 24px; clear: both;">Success Stories</h3>
                        <p>
                            Many individuals have achieved remarkable success through crowdfunding. For example, Jane Doe was able to raise funds to start her own small business, helping her to achieve financial independence and contribute to her local economy. John Smith, on the other hand, used crowdfunding to cover his medical expenses after a serious accident, easing the financial burden on his family.
                        </p>
                        <p>
                            Another inspiring story is that of a community that raised funds to build a playground for children in their neighborhood. This project not only provided a safe space for children to play but also brought the community together, fostering a sense of unity and collaboration.
                        </p>
                        <img src="https://via.placeholder.com/800x400" alt="Happy Beneficiary" class="image-container" style="float: left;" />
                        <h3 style="font-size: 24px; clear: both;">How to Get Started</h3>
                        <p>
                            Starting a crowdfunding campaign is simple. Begin by choosing a platform that aligns with your goals, create a compelling story, set a realistic funding goal, and share your campaign with your network to gain support. It's also important to keep your supporters updated on the progress of your campaign and show gratitude for their contributions.
                        </p>
                        <p>
                            Here are some key steps to follow:
                        </p>
                        <div class="accordion">
                            <h3>Choose the Right Platform</h3>
                            <p>Research various crowdfunding platforms and select one that best fits your needs. Some platforms are better suited for creative projects, while others focus on personal causes or business ventures.</p>
                            <h3>Create a Compelling Story</h3>
                            <p>Your campaign story is crucial in attracting support. Be honest, transparent, and emotional. Share your journey, the challenges you've faced, and how the funds will help you achieve your goals.</p>
                            <h3>Set a Realistic Funding Goal</h3>
                            <p>Set a funding goal that is attainable and reflects the actual cost of your project. Break down the expenses to show potential supporters where their money will go.</p>
                            <h3>Promote Your Campaign</h3>
                            <p>Utilize social media, email, and word of mouth to spread the word about your campaign. Engage with your supporters and keep them informed about your progress.</p>
                        </div>
                        <img src="https://via.placeholder.com/800x400" alt="Step-by-Step Infographic" class="image-container" />
                        <h3 style="font-size: 24px; clear: both;">Conclusion</h3>
                        <p style="font-size: 18px;">
                            Crowdfunding has the potential to change lives. By sharing our stories and supporting each other, we can make a difference.
                        </p>
                        <div class="author-bio" style="display: flex; align-items: center; margin: 2rem 0;">
                            <img src="https://via.placeholder.com/80" alt="Author Photo" width="80" height="80">
                            <div>
                                <p style="font-size: 14px; font-style: italic;">
                                    <strong>Author Name</strong> is a writer and advocate for crowdfunding. Follow on <a href="#">Twitter</a> and <a href="#">LinkedIn</a>.
                                </p>
                            </div>
                        </div>
                        <div class="social-icons" style="text-align: center; margin-top: 0.3rem; border-radius: 20rem;">
                            <h3>Spread the Word</h3>
                            <a href="#" aria-label="Share on Facebook"><img src="https://img.icons8.com/ios-glyphs/30/6D1B49/facebook.png"/></a>
                            <a href="#" aria-label="Share on Twitter"><img src="https://img.icons8.com/ios-glyphs/30/6D1B49/twitter.png"/></a>
                            <a href="#" aria-label="Share on LinkedIn"><img src="https://img.icons8.com/ios-glyphs/30/6D1B49/linkedin.png"/></a>
                        </div>
                        <div class="subscribe-container" style="border-radius: 20rem; margin-top: 1rem;">
                            <h2 style="text-align: center; font-size: 18px;">Are you seeking help? Click here to start your crowdfunding journey.</h2>
                            <form class="grid subscribe-form">
                                <input type="text" id="firstname" name="firstname" placeholder="First Name" aria-label="First Name" required />
                                <input type="tel" id="phone" name="phone" placeholder="Phone Number" aria-label="Phone Number" required />
                                <button type="submit" onclick="event.preventDefault()" style="background-color: #6D1B49;">Start Now</button>
                            </form>
                        </div>
                    </section>
                </div>
            </div>
            <div class="related-posts">
                <h3 style="font-size: 24px;">Related Posts</h3>
                <div class="card">
                    <img src="https://via.placeholder.com/250x150" alt="Related Post Thumbnail">
                    <a href="#">How Crowdfunding Helped a Small Business</a>
                    <div class="author">
                        <img src="https://via.placeholder.com/30" alt="Author">
                        <span>Author Name</span>
                    </div>
                    <div class="card-details">
                        <span>5 min read</span> • <span>Published on Jan 1, 2024</span>
                    </div>
                </div>
                <div class="card">
                    <img src="https://via.placeholder.com/250x150" alt="Related Post Thumbnail">
                    <a href="#">Top 10 Crowdfunding Platforms to Use</a>
                    <div class="author">
                        <img src="https://via.placeholder.com/30" alt="Author">
                        <span>Author Name</span>
                    </div>
                    <div class="card-details">
                        <span>8 min read</span> • <span>Published on Feb 1, 2024</span>
                    </div>
                </div>
                <div class="card">
                    <img src="https://via.placeholder.com/250x150" alt="Related Post Thumbnail">
                    <a href="#">Crowdfunding Tips for Beginners</a>
                    <div class="author">
                        <img src="https://via.placeholder.com/30" alt="Author">
                        <span>Author Name</span>
                    </div>
                    <div class="card-details">
                        <span>7 min read</span> • <span>Published on Mar 1, 2024</span>
                    </div>
                </div>
                <div class="card">
                    <img src="https://via.placeholder.com/250x150" alt="Related Post Thumbnail">
                    <a href="#">How to Create a Successful Crowdfunding Campaign</a>
                    <div class="author">
                        <img src="https://via.placeholder.com/30" alt="Author">
                        <span>Author Name</span>
                    </div>
                    <div class="card-details">
                        <span>6 min read</span> • <span>Published on Apr 1, 2024</span>
                    </div>
                </div>
            </div>
        </div>
    </main>
    <footer class="footer">
        <small>
            <a href="#">Privacy Policy</a> • <a href="#">Terms of Service</a>
        </small>
    </footer>
    <div class="popup-form">
        <h2>How can we help you? <span>&#8211;</span></h2>
        <form>
            <input type="text" name="name" placeholder="Name" required />
            <input type="tel" name="phone" placeholder="Phone Number" required />
            <select name="fund-reason" required>
                <option value="">What do you need funds for?</option>
                <option value="medical">Medical Expenses</option>
                <option value="education">Education</option>
                <option value="business">Business</option>
                <option value="personal">Personal</option>
            </select>
            <select name="language" required>
                <option value="">Preferred Language</option>
                <option value="english">English</option>
                <option value="spanish">Spanish</option>
                <option value="french">French</option>
                <option value="german">German</option>
            </select>
            <button type="submit" onclick="event.preventDefault()">Submit</button>
        </form>
    </div>
</body>
</html>
