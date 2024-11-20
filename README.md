<div align="center">
  <h1>👋 Hello, I'm Poojan Doshi</h1>
  <h2>Passionate about learning and growing!</h2>
</div>

<div align="center">
  <p><b>I specialize in:</b></p>
  <div id="skill-container" style="position: relative; width: 400px; height: 200px;">
    <!-- Typing Animation -->
    <svg width="400" height="50" xmlns="http://www.w3.org/2000/svg">
      <text x="0" y="40" fill="black" font-size="24" id="dynamic-skill">Loading...</text>
    </svg>
    
    <!-- Skill Animations -->
    <img id="skill-animation" src="https://media.giphy.com/media/l378khQxt68syiWJy/giphy.gif" 
         style="position: absolute; top: 60px; left: 0; width: 100%; display: none;" />
  </div>
</div>

<script>
  // Define skills and corresponding animations
  const skills = [
    { name: "Full-Stack Development", gif: "https://media.giphy.com/media/lP8xu5t2DLGG045H8F/giphy.gif" },
    { name: "Machine Learning", gif: "https://media.giphy.com/media/26tn33aiTi1jkl6H6/giphy.gif" },
    { name: "Data Analytics", gif: "https://media.giphy.com/media/3o7abldj0b3rxrZUxW/giphy.gif" },
    { name: "Story Writing", gif: "https://media.giphy.com/media/l378khQxt68syiWJy/giphy.gif" }
  ];

  const skillElement = document.getElementById("dynamic-skill");
  const animationElement = document.getElementById("skill-animation");

  let skillIndex = 0;
  let charIndex = 0;
  let typingForward = true;

  function typeSkill() {
    const skill = skills[skillIndex];

    if (typingForward) {
      // Typing forward
      charIndex++;
      if (charIndex > skill.name.length) {
        typingForward = false;
        setTimeout(typeSkill, 1000); // Pause before deleting
        return;
      }
    } else {
      // Deleting backward
      charIndex--;
      if (charIndex === 0) {
        typingForward = true;
        skillIndex = (skillIndex + 1) % skills.length; // Move to next skill
        setTimeout(typeSkill, 500); // Pause before typing next skill
        return;
      }
    }

    // Update skill text
    skillElement.textContent = skill.name.slice(0, charIndex);

    // Show related animation
    if (charIndex === skill.name.length) {
      animationElement.src = skill.gif;
      animationElement.style.display = "block";
    } else if (charIndex === 0) {
      animationElement.style.display = "none";
    }

    // Recursive typing
    setTimeout(typeSkill, 150);
  }

  // Start typing effect
  typeSkill();
</script>