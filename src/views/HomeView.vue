<template>
  <div class="home">
    <div id="carouselExampleIndicators" class="carousel slide" data-bs-ride="carousel">
            <div class="carousel-indicators">
              <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
              <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="1" aria-label="Slide 2"></button>
              <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="2" aria-label="Slide 3"></button>
            </div>
            <div class="carousel-inner">
              <div class="carousel-item active">
                <img src="../assets/header_drums.jpg" class="d-block w-100" alt="Photo of Bad Irony playing live.">
              </div>
              <div class="carousel-item">
                <img src="../assets/header_guitar.jpg" class="d-block w-100" alt="Photo of singer of Bad Irony singing.">
              </div>
              <div class="carousel-item">
                <img src="../assets/header_bass.jpg" class="d-block w-100" alt="Photo of bassist of Bad Irony playing live, his back towards the crowd.">
              </div>
            </div>
            <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="prev">
              <span class="carousel-control-prev-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Previous</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="next">
              <span class="carousel-control-next-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Next</span>
            </button>
    </div>

    <div class="container">
      <div class="row">
        <div class="col">
          </div>
            <div class="col">
              <img src="../assets/sphere_white.png" title="Bad Irony, est. 2019"  alt="Logo Bad Irony, est. 2019">
            </div>
          <div class="col">
        </div>
      </div>
    </div>

    <div class="container">
      <h2 class="is-size-2 has-text-centered">Upcoming Tour Dates</h2>
            <table class="table trans-table">
              <thead>
                <tr>
                  <th scope="col" class="trans-table">Location</th>
                  <th scope="col" class="trans-table">Date</th>
                  <th scope="col" class="trans-table">Tickets</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>Graz, Austria</td>
                  <td>2023-08-02</td>
                  <td><a href="https://www.eventim.de/" class="btn btn-outline-light tt" title="Go to eventim.de">Buy Tickets</a></td>
                </tr>
                <tr>
                  <td>Vienna, Austria</td>
                  <td>2023-08-03</td>
                  <td><a href="https://www.eventim.de/" class="btn btn-outline-light tt" title="Go to eventim.de">Buy Tickets</a></td>
                </tr>
                <tr>
                  <td>Munich, Germany</td>
                  <td>2023-08-05</td>
                  <td><a href="https://www.eventim.de/" class="btn btn-outline-light tt" title="Go to eventim.de">Buy Tickets</a></td>
                </tr>
              </tbody>
            </table>
            <div class="d-grid gap-2 col-3 mx-auto">
              <a href="/tour" class="btn btn-dark tt" title="Go to Tour Page">View more dates</a>
            </div>
      </div>
  </div>
</template>