const images = ["images/img1.jpg", "images/img2.jpg", "images/img3.jpg"];
let currentIndex = 0;
const sliderImage = document.getElementById("slider-image");
const dotsContainer = document.getElementById("dots-container");

function showImage(index) {
  sliderImage.src = images[index];
  updateDots(index);
}

function prevImage() {
  currentIndex = (currentIndex - 1 + images.length) % images.length;
  showImage(currentIndex);
}

function nextImage() {
  currentIndex = (currentIndex + 1) % images.length;
  showImage(currentIndex);
}

function createDots() {
  images.forEach((_, index) => {
    const dot = document.createElement("span");
    dot.classList.add("dot");
    if (index === 0) dot.classList.add("active");
    dotsContainer.appendChild(dot);
  });
}

function updateDots(index) {
  const dots = document.querySelectorAll(".dot");
  dots.forEach(dot => dot.classList.remove("active"));
  dots[index].classList.add("active");
}

// Auto-slide every 4 seconds
setInterval(() => {
  nextImage();
}, 4000);

createDots();
