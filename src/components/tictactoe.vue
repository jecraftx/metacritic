<template>
  <div class="container">
    <h1 class="text-3xl my-3 text-center font-bold">TicTacToe</h1>
    <p class="turn text-3xl font-semibold text-center my-3"></p>
    <div class="flex flex-wrap w-2/3 mx-auto">
      <div class="slot py-4 font-bold text-center w-1/3 text-3xl">&nbsp;</div>
      <div
        class="
          slot
          py-4
          font-bold
          text-center
          w-1/3
          text-3xl
          border-r-4 border-l-4 border-black
        "
      >
        &nbsp;
      </div>
      <div class="slot py-4 font-bold text-center w-1/3 text-3xl">&nbsp;</div>

      <div
        class="
          slot
          py-4
          font-bold
          text-center
          w-1/3
          text-3xl
          border-t-4 border-b-4 border-black
        "
      >
        &nbsp;
      </div>
      <div
        class="
          slot
          py-4
          font-bold
          text-center
          w-1/3
          text-3xl
          border-4 border-black
        "
      >
        &nbsp;
      </div>
      <div
        class="
          slot
          py-4
          font-bold
          text-center
          w-1/3
          text-3xl
          border-t-4 border-b-4 border-black
        "
      >
        &nbsp;
      </div>

      <div class="slot py-4 font-bold text-center w-1/3 text-3xl">&nbsp;</div>
      <div
        class="
          slot
          py-4
          font-bold
          text-center
          w-1/3
          text-3xl
          border-r-4 border-l-4 border-black
        "
      >
        &nbsp;
      </div>
      <div class="slot py-4 font-bold text-center w-1/3 text-3xl">&nbsp;</div>
    </div>
    <p class="result text-3xl font-semibold text-center mt-5"></p>
  </div>
</template>

<script>
import $ from "jquery";

export default {
  name: "TicTacToe",
  mounted() {
    var arr = ["", "", "", "", "", "", "", "", ""];
    var x = "X";
    var o = "O";
    var turn = Math.ceil(Math.random() * 2);
    var final = false;

    if (turn == 1) {
      $(".turn").html("Ход: " + x);
    } else {
      $(".turn").html("Ход: " + o);
    }

    $(".slot").each(function (index) {
      $(this).on("click", function () {
        if ($(this).text() != x && $(this).text() != o && final == false) {
          if (turn == 1) {
            $(this).html(x);
            turn = 2;
            $(".turn").html("Ход: " + o);
            arr[index] = x;
            console.log(arr);
          } else {
            $(this).html(o);
            turn = 1;
            arr[index] = o;
            console.log(arr);
            $(".turn").html("Ход: " + x);
          }
        } else {
          console.log("Данный слот уже занят либо игра закончена");
        }
        if (arr[0] == x && arr[1] == x && arr[2] == x) {
          final = true;
          $(".result").html("Победил x");
        } else if (arr[3] == x && arr[4] == x && arr[5] == x) {
          final = true;
          $(".result").html("Победил x");
        } else if (arr[6] == x && arr[7] == x && arr[8] == x) {
          final = true;
          $(".result").html("Победил x");
        } else if (arr[0] == x && arr[3] == x && arr[6] == x) {
          final = true;
          $(".result").html("Победил x");
        } else if (arr[1] == x && arr[4] == x && arr[7] == x) {
          final = true;
          $(".result").html("Победил x");
        } else if (arr[2] == x && arr[5] == x && arr[8] == x) {
          final = true;
          $(".result").html("Победил x");
        } else if (arr[0] == x && arr[4] == x && arr[8] == x) {
          final = true;
          $(".result").html("Победил x");
        } else if (arr[2] == x && arr[4] == x && arr[6] == x) {
          final = true;
          $(".result").html("Победил x");
        } else if (arr[0] == o && arr[1] == o && arr[2] == o) {
          final = true;
          $(".result").html("Победил o");
        } else if (arr[3] == o && arr[4] == o && arr[5] == o) {
          final = true;
          $(".result").html("Победил o");
        } else if (arr[6] == o && arr[7] == o && arr[8] == o) {
          final = true;
          $(".result").html("Победил o");
        } else if (arr[0] == o && arr[3] == o && arr[6] == o) {
          final = true;
          $(".result").html("Победил o");
        } else if (arr[1] == o && arr[4] == o && arr[7] == o) {
          final = true;
          $(".result").html("Победил o");
        } else if (arr[2] == o && arr[5] == o && arr[8] == o) {
          final = true;
          $(".result").html("Победил o");
        } else if (arr[0] == o && arr[4] == o && arr[8] == o) {
          final = true;
          $(".result").html("Победил o");
        } else if (arr[2] == o && arr[4] == o && arr[6] == o) {
          final = true;
          $(".result").html("Победил o");
        } else if (
          arr[0] != "" &&
          arr[1] != "" &&
          arr[2] != "" &&
          arr[3] != "" &&
          arr[4] != "" &&
          arr[5] != "" &&
          arr[6] != "" &&
          arr[7] != "" &&
          arr[8] != ""
        ) {
          final = true;
          $(".result").html("Ничья");
        }
      });
    });
  },
};
</script>