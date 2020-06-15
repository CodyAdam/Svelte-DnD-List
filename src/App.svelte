<script>
import Draggable from "./Draggable.svelte";
import SortableList from "./SortableList.svelte";
import ProgressBar from "./ProgressBar.svelte";
import ButtonCody from "./ButtonCody.svelte";

let cards = ["1e896c68-5751-4ca5-a7bb-00c0ae50b47d", "7106e96b-96e8-4b4e-aafd-f7c61baa2374", "025fda60-ccd9-4e0d-9e5a-c1cfe36f28b6", "8d83085e-a4db-4ccc-b0d2-eaa2050eca83", "1ffb576e-a6ec-404e-bcba-ad2fb84b9660", "04d02a5e-964b-4762-8dc6-5291e56a0be3", "f7c1726f-8a35-4dd6-a8cb-b914f3980a8a", "e780f9b1-6463-4d91-8d65-771c1af177c9", "0fa8be79-3dbc-4237-b5fe-8e081d0cebb5"];

const sortList = ev => {
  cards = ev.detail;
};

async function addCard() {
  try {
    loading = true;
    // await sleep(1000);
    cards = [...cards, uuidv4()];
  } catch (e) {
    alert("ERROR");
  } finally {
    loading = false;
  }

}


function uuidv4() {
  return ([1e7] + -1e3 + -4e3 + -8e3 + -1e11).replace(/[018]/g, c =>
          (c ^ crypto.getRandomValues(new Uint8Array(1))[0] & 15 >> c / 4).toString(16)
  );
}


let loading = false;


function sleep(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function deleteCard(index) {
  try {
    loading = true;
    await sleep(1000);
    let newCards = [...cards];
    newCards.splice(index, 1);
    cards = newCards;
  } catch (e) {
    alert("ERROR");
  } finally {
    loading = false;
  }


}
</script>


<main class="container">
  <ProgressBar loading="{loading}"/>


  <div class="innerContainer" style="">
    <h1>Have a list man 🤷‍</h1>


    <SortableList list={cards} on:sort={sortList} let:item let:index>
      <Draggable on:delete={() => deleteCard(index)} id={item}/>
    </SortableList>
    <div style="text-align: center">
      <ButtonCody on:click="{addCard}" loading="{loading}">+</ButtonCody>
      <!--    <button class="plus" on:click="{addCard}">+</button>-->
    </div>

  </div>


</main>


<style lang="scss">
  .container {
    height: 90%;
    position: relative;
    max-width: 500px;
    overflow: hidden;
    border-radius: 10px;

    @media (max-width: 1000px) {

      height: 100%;
      border-radius: 0;

    }

    &:before, &:after {
      content: ' ';
      position: absolute;
      left: 0;
      right: 17px;
      height: 10%;
      pointer-events: none;
      z-index: 1;
    }

    &:before {
      bottom: 90%;
      background: linear-gradient(180deg, rgba(45, 45, 45, 1) 0%, rgba(45, 45, 45, 0) 100%);
    }

    &:after {
      top: 90%;
      background: linear-gradient(0deg, rgba(45, 45, 45, 1) 0%, rgba(45, 45, 45, 0) 100%);
    }
  }


  .innerContainer {
    position: relative;
    padding: 20px;
    background-color: #2d2d2d;

    overflow-x: hidden;
    overflow-y: scroll;
    height: 100%
  }


</style>
