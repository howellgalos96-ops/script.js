# script.js
asawako
const yesBtn = document.getElementById('yesBtn');
const noBtn = document.getElementById('noBtn');
const messageArea = document.getElementById('messageArea');
const floating = document.getElementById('floating');

// Floating hearts and flowers
function createFloatingItem() {
    const item = document.createElement('div');
    item.classList.add('floating');
    const shapes = ['💖','🌸','🌹','💘','🌺','💗','💞'];
    item.textContent = shapes[Math.floor(Math.random() * shapes.length)];
    item.style.left = Math.random() * window.innerWidth + 'px';
    item.style.fontSize = (20 + Math.random()*30) + 'px';
    item.style.animationDuration = (5 + Math.random()*5) + 's';
    floating.appendChild(item);
    setTimeout(() => item.remove(), 12000);
}

// continuously generate floating items
setInterval(createFloatingItem, 400);

// Heart explosion effect for Yes button
function heartExplosion(x, y) {
    for (let i = 0; i < 30; i++) {
        const heart = document.createElement('div');
        heart.classList.add('floating');
        const shapes = ['💖','💗','💘','💞'];
        heart.textContent = shapes[Math.floor(Math.random() * shapes.length)];
        heart.style.left = x + (Math.random()*100 - 50) + 'px';
        heart.style.top = y + (Math.random()*100 - 50) + 'px';
        heart.style.fontSize = (15 + Math.random()*20) + 'px';
        heart.style.animationDuration = (2 + Math.random()*2) + 's';
        floating.appendChild(heart);
        setTimeout(() => heart.remove(), 4000);
    }
}

// Yes Button Event
yesBtn.addEventListener('click', (e) => {
    const rect = e.target.getBoundingClientRect();
    heartExplosion(rect.left + rect.width/2, rect.top + rect.height/2);

    messageArea.innerHTML = `
        <p>💖 Yay! I'm so happy you'll be my Valentine! 💖</p>
        <img src="a07147ce-9519-425c-809f-ac972729355c.png" alt="My Love">
        <p class="secret">I love you more than words can say. ❤️ Forever yours.</p>
    `;
});

// No Button Event
noBtn.addEventListener('click', () => {
    messageArea.innerHTML = `<p>Oops! 😢 Try again!</p>`;
});
