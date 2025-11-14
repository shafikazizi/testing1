document.getElementById('bookingForm').addEventListener('submit', function(e) {
  e.preventDefault();
  const nama = document.getElementById('nama').value;
  const kereta = document.getElementById('kereta').value;
  const tarikh = document.getElementById('tarikh').value;
  const masa = document.getElementById('masa').value;

  if(nama && kereta && tarikh && masa) {
    document.getElementById('status').innerHTML = `
      <div class="alert alert-success">Tempahan berjaya untuk ${kereta} pada ${tarikh} jam ${masa} oleh ${nama}.</div>
    `;
    this.reset();
  } else {
    document.getElementById('status').innerHTML = `
      <div class="alert alert-danger">Sila isi semua maklumat!</div>
    `;
  }
});
