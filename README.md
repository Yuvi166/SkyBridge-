# SkyBridge-
Travel booking 

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>SkyBridge - Flight Booking</title>
<style>
  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: #f5f8fa;
    margin: 0;
    padding: 0;
  }
  header {
    background: #004aad;
    color: white;
    padding: 15px 20px;
    text-align: center;
  }
  main {
    max-width: 600px;
    margin: 40px auto;
    background: white;
    padding: 30px;
    box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    border-radius: 8px;
  }
  label {
    display: block;
    margin-bottom: 8px;
    font-weight: 600;
  }
  input, select {
    width: 100%;
    padding: 10px;
    margin-bottom: 20px;
    border-radius: 4px;
    border: 1px solid #ddd;
    font-size: 16px;
  }
  button {
    background-color: #004aad;
    color: white;
    font-weight: 700;
    padding: 12px;
    width: 100%;
    border: none;
    border-radius: 6px;
    font-size: 18px;
    cursor: pointer;
  }
  button:hover {
    background-color: #003080;
  }
  footer {
    text-align: center;
    margin-top: 40px;
    color: #888;
    font-size: 14px;
  }
</style>
</head>
<body>

<header>
  <h1>SkyBridge - Book Flights with Ease</h1>
</header>

<main>
  <form id="flightForm">
    <label for="from">From (City or Airport Code)</label>
    <input type="text" id="from" name="from" placeholder="e.g. DEL, New Delhi" required />

    <label for="to">To (City or Airport Code)</label>
    <input type="text" id="to" name="to" placeholder="e.g. BOM, Mumbai" required />

    <label for="departDate">Departure Date</label>
    <input type="date" id="departDate" name="departDate" required />

    <label for="returnDate">Return Date (Optional)</label>
    <input type="date" id="returnDate" name="returnDate" />

    <label for="passengers">Passengers</label>
    <select id="passengers" name="passengers">
      <option value="1">1</option>
      <option value="2" selected>2</option>
      <option value="3">3</option>
      <option value="4">4</option>
    </select>

    <button type="submit">Search Flights</button>
  </form>
</main>

<footer>
  &copy; 2025 SkyBridge Travel. All rights reserved.
</footer>

<script>
  const affiliateBase = 'https://tp.media/r?marker=636182&trs=421728&p=5976&u=https%3A%2F%2Fwayaway.io&campaign_id=200';

  document.getElementById('flightForm').addEventListener('submit', function(e) {
    e.preventDefault();

    const from = encodeURIComponent(document.getElementById('from').value.trim());
    const to = encodeURIComponent(document.getElementById('to').value.trim());
    const depart = document.getElementById('departDate').value;
    const ret = document.getElementById('returnDate').value;
    const passengers = document.getElementById('passengers').value;

    // Build query params WayAway expects (adjust if API requires different params)
    let searchUrl = 'https://wayaway.io/flights?';
    searchUrl += `origin=${from}&destination=${to}&depart_date=${depart}`;

    if (ret) {
      searchUrl += `&return_date=${ret}`;
    }
    searchUrl += `&passengers=${passengers}`;

    // Combine affiliate redirect
    const finalUrl = affiliateBase + encodeURIComponent(searchUrl);

    // Redirect user to affiliate link with embedded flight search params
    window.location.href = finalUrl;
  });
</script>

</body>
</html>


---

2. hotels.html (Hotels Page)

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>SkyBridge - Hotel Booking</title>
<style>
  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: #f5f8fa;
    margin: 0;
    padding: 0;
  }
  header {
    background: #004aad;
    color: white;
    padding: 15px 20px;
    text-align: center;
  }
  main {
    max-width: 600px;
    margin: 40px auto;
    background: white;
    padding: 30px;
    box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    border-radius: 8px;
  }
  label {
    display: block;
    margin-bottom: 8px;
    font-weight: 600;
  }
  input {
    width: 100%;
    padding: 10px;
    margin-bottom: 20px;
    border-radius: 4px;
    border: 1px solid #ddd;
    font-size: 16px;
  }
  button {
    background-color: #004aad;
    color: white;
    font-weight: 700;
    padding: 12px;
    width: 100%;
    border: none;
    border-radius: 6px;
    font-size: 18px;
    cursor: pointer;
  }
  button:hover {
    background-color: #003080;
  }
  footer {
    text-align: center;
    margin-top: 40px;
    color: #888;
    font-size: 14px;
  }
</style>
</head>
<body>

<header>
  <h1>SkyBridge - Book Hotels</h1>
</header>

<main>
  <form id="hotelForm">
    <label for="location">City or Hotel Name</label>
    <input type="text" id="location" name="location" placeholder="e.g. Jaipur, Mumbai" required />

    <label for="checkin">Check-in Date</label>
    <input type="date" id="checkin" name="checkin" required />

    <label for="checkout">Check-out Date</label>
    <input type="date" id="checkout" name="checkout" required />

    <button type="submit">Search Hotels</button>
  </form>
</main>

<footer>
  &copy; 2025 SkyBridge Travel. All rights reserved.
</footer>

<script>
  const affiliateBase = 'https://tp.media/r?marker=636182&trs=421728&p=5976&u=https%3A%2F%2Fwayaway.io&campaign_id=200';

  document.getElementById('hotelForm').addEventListener('submit', function(e) {
    e.preventDefault();

    const location = encodeURIComponent(document.getElementById('location').value.trim());
    const checkin = document.getElementById('checkin').value;
    const checkout = document.getElementById('checkout').value;

    let searchUrl = `https://wayaway.io/hotels?location=${location}&checkin=${checkin}&checkout=${checkout}`;

    const finalUrl = affiliateBase + encodeURIComponent(searchUrl);

    window.location.href = finalUrl;
  });
</script>

</body>
</html>
