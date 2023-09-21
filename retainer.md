// Prompt the user for card information
    const divClass = prompt("Enter a CSS class for the card, only lowercase letters with no space (replaced by -):");
    const animeName = prompt("Enter the anime name:");
    const author = prompt("Enter the author:");
    const genreString = prompt("Enter genres (comma-separated):");
    const genre = genreString.split(',').map(item => item.trim());
    const image = prompt("Enter the image URL:");
    const date = prompt("Enter the release date:");
    const description = prompt("Enter the description:");
    const link = prompt("Enter the MyAnimeList link:");

    const collection = document.querySelector('.container');

    // Create a new card div
    const newDiv = document.createElement('div');
    newDiv.classList.add(divClass);

    // Create an image element
    const newImg = document.createElement('img');
    newImg.src = image;
    newImg.style.width = '90%';
    newImg.style.margin = '20px auto 10px auto';
    newDiv.appendChild(newImg);

    // Create a div for genre buttons
    const buttonDiv = document.createElement('div');
    buttonDiv.classList.add('buttonDiv');
    for (const genreItem of genre) {
        const newButton = document.createElement('button');
        newButton.textContent = genreItem;
        buttonDiv.appendChild(newButton);
    }
    newDiv.appendChild(buttonDiv);

    // Create a span for anime name
    const newspanName = document.createElement('span');
    newspanName.classList.add('name');
    newspanName.textContent = animeName;
    newDiv.appendChild(newspanName);

    // Create a span for author
    const newspanAuthor = document.createElement('span');
    newspanAuthor.classList.add('author');
    newspanAuthor.textContent = author;
    newDiv.appendChild(newspanAuthor);

    // Create a span for date
    const newspanDate = document.createElement('span');
    newspanDate.textContent = date;
    newDiv.appendChild(newspanDate);

    // Create a paragraph for description
    const newP = document.createElement('p');
    newP.classList.add('text');
    newP.textContent = description;
    newDiv.appendChild(newP);

    // Create a div for links (e.g., MyAnimeList)
    const lignDiv = document.createElement('div');
    lignDiv.classList.add('lignDiv');

    // Create a div for MyAnimeList logo
    const malDiv = document.createElement('div');
    malDiv.classList.add('malLogo');
    const malA = document.createElement('a');
    malA.classList.add('malA');
    malA.href = link;
    malA.target = '_blank';
    const malSVG = document.createElement('img');
    malSVG.classList.add('malSVG');
    malSVG.src = 'imgs/myanimelist.svg';
    malA.appendChild(malSVG);
    malDiv.appendChild(malA);

    // Create a delete button
    const deleteDiv = document.createElement('div');
    deleteDiv.classList.add('deleteButton');
    const deleteButton = document.createElement('button');
    deleteButton.classList.add('deleteDesign');
    deleteButton.textContent = 'Delete';
    deleteDiv.appendChild(deleteButton);

    // Create a div for delete button and MyAnimeList logo
    const deletelogoDiv = document.createElement('div');
    deletelogoDiv.classList.add('deleteLogoDiv');
    deletelogoDiv.appendChild(deleteDiv);
    deletelogoDiv.appendChild(malDiv);

    newDiv.appendChild(deletelogoDiv);

    // Append the new card to the container
    collection.appendChild(newDiv);

    // Add an event listener to the delete button
    deleteButton.addEventListener("click", function(e) {
        this.parentNode.parentNode.parentNode.remove();
    });