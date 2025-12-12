<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <link rel="icon" href="/public/cake.png" type="image/x-icon" />
    <link rel="icon" type="image/png" href="confetti.png" />
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC"
      crossorigin="anonymous"
    />

    <title>Happy Birthday</title>
  </head>
  <body>
    <div class="position-absolute top-50 start-50 translate-middle">
      <button
        id="button"
        class="btn btn-primary btn-lg"
        onclick="mulai();music()"
      >
        Click Here!
      </button>
      <div id="iloveyou" style="display: none">
        <h2 id="birthdayMessage" class="text-center">
          Happy Birthday <span id="birthdayName"></span>
        </h2>
        <h2 class="text-center">&#x1F389;</h2>
      </div>
    </div>
    <span
      id="hati"
      class="fixed-bottom text-center my-3"
      onclick="hati()"
    ></span>
    <audio id="bgMusic" src="music/selamatulangtahun.mp3" loop></audio>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11.0.19/dist/sweetalert2.all.min.js"></script>
    <script type="text/javascript">
      const author = "Someone";
      document.getElementById(
        "hati"
      ).innerHTML = `Made with &#x1F499; by ${author}`;
      const swals = Swal.mixin({
        cancelButtonColor: "#d33",
        confirmButtonColor: "#3085d6",
      });

      function stopMusic() {
        var audio = document.getElementById("bgMusic");
        audio.pause();
        audioPlaying = false;
      }

      async function mulai() {
        await swals.fire(
          "Hayy!",
          "Karena hari ini ada orang spesial yang lahir kedunia...",
          "question"
        );
        await swals.fire("Aku mau ngucapin sesuatu nih hehe");

        var { value: nama } = await swals.fire({
          title: "Oh yaa  tulis nama sek yaa",
          input: "text",
        });

        if (!nama) {
          stopMusic();
          return;
        }

        document.getElementById("birthdayName").textContent = nama;
        var { isConfirmed: sayang } = await swals.fire({
          title: `${nama} hari ini kamu tambah tuwek yaa?`,
          confirmButtonText: "Iya",
          cancelButtonText: "Ngak",
          showCancelButton: true,
        });

        if (!sayang) {
          stopMusic();
          return;
        }

        await swals.fire("Cie.. udah tambah tuwek aja nih hehe");

        var { value: persen } = await swals.fire({
          title: "Hari ini kamu yang cantik ini umur berapa sihh...?",
          icon: "question",
          input: "range",
          inputAttributes: {
            min: 1,
            max: 63,
          },
          inputValue: 10,
        });

        if (!persen) {
          stopMusic();
          return;
        }

        await swals.fire(
          `wahh udah ${persen} aja nih,semoga diumur yang semakin tuwek ini kamu semakin dewasa dalam menghadapi kehidupan :)`
        );

        var { isConfirmed: kangen } = await swals.fire({
          title:
            "Dan semoga di umurmu yang semakin tuwek ini kamu bisa mencapai semua mimpi-mimpimu yaaaa....",
          confirmButtonText: "Aamiin",
        });

        if (!kangen) {
          stopMusic();
          return;
        }

        await swals.fire(
          "dahlah,cuma mau ngucapin itu aja,semangat terus ya cantik hehe :)"
        );
        await swals.fire(`Oh iya ${nama} terakhir nih`);
        await swals.fire("karena aku malu ngetik langsung aku mau bulang disini aja will you be my girl friend?   dijawab yaa.. oh sama terakhir nih klik ikon love dibawah yaa   dadah ");
      }

      var audioPlaying = false;
      function music() {
        var audio = document.getElementById("bgMusic");
        if (!audioPlaying) audio.play();
        else audio.pause();
        audioPlaying = !audioPlaying;
      }

      function hati() {
        document.getElementById("button").style = "display: none";
        document.getElementById("iloveyou").style = "";
        startConfetti();
      }
    </script>

    <script
      type="text/javascript"
      src="https://www.cssscript.com/demo/confetti-falling-animation/confetti.js"
    ></script>
    <!-- <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script> -->
  </body>
</html>


