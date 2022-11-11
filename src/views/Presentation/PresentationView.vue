<script>
export default {
    data(){
        return{
          sido: '도시 선택',
          gugun: '구 선택',
          dong: '동 선택'

        }
    },
    methods: {
      changeSido(inputSido) {
        return this.sido = inputSido;
      },
      changeGugun(inputGugun) {
        return this.gugun = inputGugun;
      },
      changeDong(inputDong) {
        return this.dong = inputDong;
      }


    },
    
}
</script>


<script setup>
import { onMounted, onUnmounted } from "vue";

//example components
import NavbarDefault from "../..//examples/navbars/NavbarDefault.vue";
import DefaultFooter from "../../examples/footers/FooterDefault.vue";
import Header from "../../examples/Header.vue";

//Vue Material Kit 2 components
import MaterialSocialButton from "@/components/MaterialSocialButton.vue";

// sections
// import PresentationPages from "./Sections/PresentationPages.vue";
import BuiltByDevelopers from "./Components/BuiltByDevelopers.vue";
import PresentationInformation from "./Sections/PresentationInformation.vue";

//images
import vueMkHeader from "@/assets/img/bg1.jpg";
import wavesWhite from "@/assets/img/waves-white.svg";
import logoBootstrap from "@/assets/img/logos/bootstrap5.jpg";
import logoTailwind from "@/assets/img/logos/icon-tailwind.jpg";
import logoVue from "@/assets/img/logos/vue.jpg";
import logoAngular from "@/assets/img/logos/angular.jpg";
import logoReact from "@/assets/img/logos/react.jpg";
import logoSketch from "@/assets/img/logos/sketch.jpg";




//Temp import
import MaterialInput from "@/components/MaterialInput.vue";
import MaterialButton from "@/components/MaterialButton.vue";
import setMaterialInput from "@/assets/js/material-input";
import Typed from "typed.js";


//hooks
const body = document.getElementsByTagName("body")[0];
onMounted(() => {
  setMaterialInput();
  body.classList.add("presentation-page");
  body.classList.add("bg-gray-200");
  if (document.getElementById("typed")) {
    // eslint-disable-next-line no-unused-vars
    var typed = new Typed("#typed", {
      stringsElement: "#typed-strings",
      typeSpeed: 90,
      backSpeed: 120,
      backDelay: 200,
      startDelay: 500,
      loop: true,
    });
  }
});
onUnmounted(() => {
  body.classList.remove("presentation-page");
  body.classList.remove("bg-gray-200");
});



</script>

<template>
  <div class="container position-sticky z-index-sticky top-0">
    <div class="row">
      <div class="col-12">
        <NavbarDefault :sticky="true" />
      </div>
    </div>
  </div>
  <Header>
    <div
      class="page-header min-vh-75"
      :style="`background-image: url(${vueMkHeader})`"
      loading="lazy"
    >
      <div class="container">
        <div class="row">
          <div class="col-lg-7 text-center mx-auto position-relative">

            <p class="lead text-black px-5 mt-3" :style="{ fontWeight: '500' }">
              <h3>
                 <span class="text-white" id="typed"></span>
              </h3>
              <div id="typed-strings">
                <h1> #내집마련</h1>
                <h1> #집찾아줘</h1>
                <h1> #구해줘홈즈</h1>
                <h1> #가격실화냐</h1>
              </div>          
            </p>

        <div id = "selectSido" class="d-inline p-4">
          <MaterialButton
              variant="gradient"
              color="success"
              class="dropdown-toggle"
              :class="{ show: showDropdown }"
              @focusout="showDropdown = false"
              id="dropdownMenuButton"
              data-bs-toggle="dropdown"
              :area-expanded="showDropdown"
              @click="showDropdown = !showDropdown"
            >
              {{sido}}
            </MaterialButton>

            <ul
              class="dropdown-menu px-2 py-3"
              :class="{ show: showDropdown }"
              aria-labelledby="dropdownMenuButton"
            >
              <li>
                <a class="dropdown-item border-radius-md" href="javascript:;" 
                @click="changeSido('서울특별시')">
                  서울
                  </a>
              </li>
              <li>
                <a class="dropdown-item border-radius-md" href="javascript:;"
                @click="changeSido('부산광역시')">
                부산</a>
              </li>
            </ul>
        </div>

        <div id = "selectGugun" class="d-inline p-4">
          <MaterialButton
              variant="gradient"
              color="success"
              class="dropdown-toggle"
              :class="{ show: showDropdown }"
              @focusout="showDropdown = false"
              id="dropdownMenuButton"
              data-bs-toggle="dropdown"
              :area-expanded="showDropdown"
              @click="showDropdown = !showDropdown"
            >
              {{gugun}}
            </MaterialButton>

            <ul
              class="dropdown-menu px-2 py-3"
              :class="{ show: showDropdown }"
              aria-labelledby="dropdownMenuButton"
            >
              <li>
                <a class="dropdown-item border-radius-md" href="javascript:;" 
                @click="changeGugun('용산구')">
                  용산구
                  </a>
              </li>
              <li>
                <a class="dropdown-item border-radius-md" href="javascript:;"
                @click="changeGugun('부산진구')">
                부산진구</a>
              </li>
            </ul>
        </div>

        <div id = "selectDong" class="d-inline p-4">
          <MaterialButton
              variant="gradient"
              color="success"
              class="dropdown-toggle"
              :class="{ show: showDropdown }"
              @focusout="showDropdown = false"
              id="dropdownMenuButton"
              data-bs-toggle="dropdown"
              :area-expanded="showDropdown"
              @click="showDropdown = !showDropdown"
            >
              {{dong}}
            </MaterialButton>

            <ul
              class="dropdown-menu px-2 py-3"
              :class="{ show: showDropdown }"
              aria-labelledby="dropdownMenuButton"
            >
              <li>
                <a class="dropdown-item border-radius-md" href="javascript:;" 
                @click="changeDong('역삼동')">
                  역삼동
                  </a>
              </li>
              <li>
                <a class="dropdown-item border-radius-md" href="javascript:;"
                @click="changeDong('가야동')">
                가야동</a>
              </li>
            </ul>
        </div>

        <div id = "searchButton" class="d-inline p-4">
          <MaterialButton
            variant="gradient"
            color="success">
            Subscribe
            </MaterialButton>
        </div>


    <br><br><br>
      <!-- 아파트 이름으로 검색하는 input창인데 쓸지 안쓸지 모름-->
        <div>
          <MaterialInput
              class="input-group-outline"
              id="email"
              :label="{ text: 'Email Here...', class: 'form-label' }"
              type="email"
            />
        </div>





          </div>
        </div>
      </div>
    </div>
  
  </Header>

  <div class="card card-body blur shadow-blur mx-3 mx-md-4 mt-n6">

   <!-- <PresentationCounter />-->
    <PresentationInformation />
    

      <!--
    <BuiltByDevelopers />
  <PresentationTestimonials /> -->
  </div>
  <DefaultFooter />
</template>
