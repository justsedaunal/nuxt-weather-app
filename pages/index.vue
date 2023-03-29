<template>
  <section class="vh-100 container ">
    <!-- input area start  -->
    <!-- <div class="input-group mt-4">
      <div class="form-outline">
        <input
          type="search"
          id="form1"
          class="form-control"
          style="background-color: #e1f5fe"
        />
        <label class="form-label" for="form1">Search</label>
      </div>
      <button type="button" class="btn btn-primary" @click="getCurrentLocation">
        <i class="fas fa-search"></i>
      </button>
    </div> -->
    <!-- input area end  -->
    <div class="container justify-content-center d-flex background-animation">
      <div class="d-flex flex-column justify-content-center align-items-center">
        <!-- main cart area start  -->
        <div
          class="row d-flex justify-content-center align-items-center mt-4 w-100"
        >
          <div v-if="data.name" class="" v-show="data.length != 0">
            <div class="card" style="color: #4b515d; border-radius: 35px">
              <div class="card-body p-4">
                <div class="d-flex">
                  <h6 class="flex-grow-1">{{ data.name }}</h6>
                  <h6>{{ currentDate() }}</h6>
                </div>

                <div class="d-flex flex-column text-center mt-5 mb-4">
                  <h6
                    class="display-4 mb-0 font-weight-bold"
                    style="color: #1c2331"
                  >
                    {{  Math.floor (data.main.temp -272.15)   }} 
                    °

                  </h6>
                  <span class="small" style="color: #868b94"
                    >{{ data.weather[0].main }}
                    <!-- rain -->
                  </span>
                  <span class="small" style="color: #868b94"
                    >{{ data.weather[0].description }}
                  </span>

                  <div>
                    <img
                      :src="
                        images.find(
                          (image) => image.alt === data.weather[0].main
                        )?.url
                      "
                      class="img-responsive"
                    />
                  </div>
                  <!-- render icns start -->
                </div>
                <!-- render icns end -->

                <div
                  class="d-flex justify-content-between align-items-center"
                  style="font-size: 1rem"
                >
                  <div
                    class="d-flex flex-column justify-content-between align-items-center"
                  >
                    <span class="ms-1"> wind speed </span>

                    <img src="../assets/wind-beaufort-1.svg" width="100px" />
                    <span class="ms-1"> {{ data.wind.speed }} km/h </span>
                  </div>
                  <div
                    class="d-flex flex-column justify-content-between align-items-center"
                  >
                    <span class="ms-1"> humidity</span>

                    <img src="../assets/humidity.svg" width="100px" />

                    <span class="ms-1"> {{ data.main.humidity }} % </span>
                  </div>
                  <div
                    class="d-flex flex-column justify-content-between align-items-center"
                  >
                    <span class="ms-1"> pressure </span>
                    <img src="../assets/pressure-high.svg" width="100px" />
                    <span class="ms-1"> {{ data.main.pressure }} hpa</span>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <!-- loader start -->

          <div class="preloader" style="opacity: 1" v-else="data">
            <svg
              version="1.1"
              id="sun"
              xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink"
              x="0px"
              y="0px"
              width="10px"
              height="10px"
              viewBox="0 0 10 10"
              enable-background="new 0 0 10 10"
              xml:space="preserve"
              style="opacity: 1; margin-left: 0px; margin-top: 0px"
            >
              <g>
                <path
                  fill="none"
                  d="M6.942,3.876c-0.4-0.692-1.146-1.123-1.946-1.123c-0.392,0-0.779,0.104-1.121,0.301c-1.072,0.619-1.44,1.994-0.821,3.067C3.454,6.815,4.2,7.245,5,7.245c0.392,0,0.779-0.104,1.121-0.301C6.64,6.644,7.013,6.159,7.167,5.581C7.321,5,7.243,4.396,6.942,3.876z M6.88,5.505C6.745,6.007,6.423,6.427,5.973,6.688C5.676,6.858,5.34,6.948,5,6.948c-0.695,0-1.343-0.373-1.69-0.975C2.774,5.043,3.093,3.849,4.024,3.312C4.32,3.14,4.656,3.05,4.996,3.05c0.695,0,1.342,0.374,1.69,0.975C6.946,4.476,7.015,5,6.88,5.505z"
                ></path>
                <path
                  fill="none"
                  d="M8.759,2.828C8.718,2.757,8.626,2.732,8.556,2.774L7.345,3.473c-0.07,0.041-0.094,0.132-0.053,0.202C7.319,3.723,7.368,3.75,7.419,3.75c0.025,0,0.053-0.007,0.074-0.02l1.211-0.699C8.774,2.989,8.8,2.899,8.759,2.828z"
                ></path>
                <path
                  fill="none"
                  d="M1.238,7.171c0.027,0.047,0.077,0.074,0.128,0.074c0.025,0,0.051-0.008,0.074-0.02l1.211-0.699c0.071-0.041,0.095-0.133,0.054-0.203S2.574,6.228,2.503,6.269l-1.21,0.699C1.221,7.009,1.197,7.101,1.238,7.171z"
                ></path>
                <path
                  fill="none"
                  d="M6.396,2.726c0.052,0,0.102-0.026,0.13-0.075l0.349-0.605C6.915,1.976,6.89,1.885,6.819,1.844c-0.07-0.042-0.162-0.017-0.202,0.054L6.269,2.503C6.228,2.574,6.251,2.666,6.322,2.706C6.346,2.719,6.371,2.726,6.396,2.726z"
                ></path>
                <path
                  fill="none"
                  d="M3.472,7.347L3.123,7.952c-0.041,0.07-0.017,0.162,0.054,0.203C3.2,8.169,3.226,8.175,3.25,8.175c0.052,0,0.102-0.027,0.129-0.074l0.349-0.605c0.041-0.07,0.017-0.16-0.054-0.203C3.603,7.251,3.513,7.276,3.472,7.347z"
                ></path>
                <path
                  fill="none"
                  d="M3.601,2.726c0.025,0,0.051-0.007,0.074-0.02C3.746,2.666,3.77,2.574,3.729,2.503l-0.35-0.604C3.338,1.828,3.248,1.804,3.177,1.844C3.106,1.886,3.082,1.976,3.123,2.047l0.35,0.604C3.5,2.7,3.549,2.726,3.601,2.726z"
                ></path>
                <path
                  fill="none"
                  d="M6.321,7.292c-0.07,0.043-0.094,0.133-0.054,0.203l0.351,0.605c0.026,0.047,0.076,0.074,0.127,0.074c0.025,0,0.051-0.006,0.074-0.02c0.072-0.041,0.096-0.133,0.055-0.203l-0.35-0.605C6.483,7.276,6.393,7.253,6.321,7.292z"
                ></path>
                <path
                  fill="none"
                  d="M2.202,5.146c0.082,0,0.149-0.065,0.149-0.147S2.284,4.851,2.202,4.851H1.503c-0.082,0-0.148,0.066-0.148,0.148s0.066,0.147,0.148,0.147H2.202z"
                ></path>
                <path
                  fill="none"
                  d="M8.493,4.851H7.794c-0.082,0-0.148,0.066-0.148,0.148s0.066,0.147,0.148,0.147l0,0h0.699c0.082,0,0.148-0.065,0.148-0.147S8.575,4.851,8.493,4.851L8.493,4.851z"
                ></path>
                <path
                  fill="none"
                  d="M5.146,2.203V0.805c0-0.082-0.066-0.148-0.148-0.148c-0.082,0-0.148,0.066-0.148,0.148v1.398c0,0.082,0.066,0.149,0.148,0.149C5.08,2.352,5.146,2.285,5.146,2.203z"
                ></path>
                <path
                  fill="none"
                  d="M4.85,7.796v1.396c0,0.082,0.066,0.15,0.148,0.15c0.082,0,0.148-0.068,0.148-0.15V7.796c0-0.082-0.066-0.148-0.148-0.148C4.917,7.647,4.85,7.714,4.85,7.796z"
                ></path>
                <path
                  fill="none"
                  d="M2.651,3.473L1.44,2.774C1.369,2.732,1.279,2.757,1.238,2.828C1.197,2.899,1.221,2.989,1.292,3.031l1.21,0.699c0.023,0.013,0.049,0.02,0.074,0.02c0.051,0,0.101-0.026,0.129-0.075C2.747,3.604,2.722,3.514,2.651,3.473z"
                ></path>
                <path
                  fill="none"
                  d="M8.704,6.968L7.493,6.269c-0.07-0.041-0.162-0.016-0.201,0.055c-0.041,0.07-0.018,0.162,0.053,0.203l1.211,0.699c0.023,0.012,0.049,0.02,0.074,0.02c0.051,0,0.102-0.027,0.129-0.074C8.8,7.101,8.776,7.009,8.704,6.968z"
                ></path>
              </g>
            </svg>

            <svg
              version="1.1"
              id="cloud"
              xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink"
              x="0px"
              y="0px"
              width="10px"
              height="10px"
              viewBox="0 0 10 10"
              enable-background="new 0 0 10 10"
              xml:space="preserve"
            >
              <path
                fill="none"
                d="M8.528,5.624H8.247c-0.085,0-0.156-0.068-0.156-0.154c0-0.694-0.563-1.257-1.257-1.257c-0.098,0-0.197,0.013-0.3,0.038C6.493,4.259,6.45,4.252,6.415,4.229C6.38,4.208,6.356,4.172,6.348,4.131C6.117,3.032,5.135,2.235,4.01,2.235c-1.252,0-2.297,0.979-2.379,2.23c-0.004,0.056-0.039,0.108-0.093,0.13C1.076,4.793,0.776,5.249,0.776,5.752c0,0.693,0.564,1.257,1.257,1.257h6.495c0.383,0,0.695-0.31,0.695-0.692S8.911,5.624,8.528,5.624z"
              ></path>
            </svg>

            <div class="rain">
              <span class="drop"></span>
              <span class="drop"></span>
              <span class="drop"></span>
              <span class="drop"></span>
              <span class="drop"></span>
              <span class="drop"></span>
              <span class="drop"></span>
              <span class="drop"></span>
              <span class="drop"></span>
              <span class="drop"></span>
            </div>

            <div class="text">LOOKING OUTSIDE FOR YOU... ONE SEC</div>
          </div>
          <!-- loader end -->
        </div>
        <!-- main cart area end  -->

        <!-- forecaste cart area start  -->
        <div class="d-flex gap-2 justify-content-center flex-wrap mb-4">
          <div class="d-flex" v-for="(item, i) in forecasteData">
            <div
              class="row d-flex justify-content-center align-items-center mt-4 w-md-100"
            >
              <div v-if="data.name" class="" v-show="data.length != 0">
                <div class="card" style="color: #4b515d; border-radius: 35px">
                  <div class="card-body">
                   

                    <div class="d-flex flex-column text-center mt-5 mb-4">
                      <div class="d-flex align-items-center justify-content-center" >
                        <h6
                        class="display-4 mb-0 font-weight-bold font-size"
                        style="color: #1c2331"
                      >
                        {{ Math.floor(forecasteData[i].main.temp -272.15) }} 
                        °
                      </h6>

                      </div>
                 

                      <div>
                        <img
                          :src="
                            images.find(
                              (image) =>
                                image.alt === forecasteData[i].weather[0].main
                            )?.url
                          "
                          width="100px"
                        />
                      </div>
                    </div>

                    <div
                      class="d-flex justify-content-between align-items-center"
                      style="font-size: 1rem"
                    >
                      <div>
                        <span class="ms-1">
                          {{
                            new Intl.DateTimeFormat("en-US", {
                              weekday: "short",
                            }).format(new Date(forecasteData[i].dt_txt))
                          }}</span
                        >
                      </div>
                    </div>
                    <div>
                      <!-- <img
                    src="https://bmcdn.nl/assets/weather-icons/v3.0/fill/svg/cloudy.svg"
                    width="100px"
                  /> -->
                    </div>
                  </div>
                </div>
              </div>

              <!-- loader start -->

              <div class="preloader" style="opacity: 1" v-else="data">
                <svg
                  version="1.1"
                  id="sun"
                  xmlns="http://www.w3.org/2000/svg"
                  xmlns:xlink="http://www.w3.org/1999/xlink"
                  x="0px"
                  y="0px"
                  width="10px"
                  height="10px"
                  viewBox="0 0 10 10"
                  enable-background="new 0 0 10 10"
                  xml:space="preserve"
                  style="opacity: 1; margin-left: 0px; margin-top: 0px"
                >
                  <g>
                    <path
                      fill="none"
                      d="M6.942,3.876c-0.4-0.692-1.146-1.123-1.946-1.123c-0.392,0-0.779,0.104-1.121,0.301c-1.072,0.619-1.44,1.994-0.821,3.067C3.454,6.815,4.2,7.245,5,7.245c0.392,0,0.779-0.104,1.121-0.301C6.64,6.644,7.013,6.159,7.167,5.581C7.321,5,7.243,4.396,6.942,3.876z M6.88,5.505C6.745,6.007,6.423,6.427,5.973,6.688C5.676,6.858,5.34,6.948,5,6.948c-0.695,0-1.343-0.373-1.69-0.975C2.774,5.043,3.093,3.849,4.024,3.312C4.32,3.14,4.656,3.05,4.996,3.05c0.695,0,1.342,0.374,1.69,0.975C6.946,4.476,7.015,5,6.88,5.505z"
                    ></path>
                    <path
                      fill="none"
                      d="M8.759,2.828C8.718,2.757,8.626,2.732,8.556,2.774L7.345,3.473c-0.07,0.041-0.094,0.132-0.053,0.202C7.319,3.723,7.368,3.75,7.419,3.75c0.025,0,0.053-0.007,0.074-0.02l1.211-0.699C8.774,2.989,8.8,2.899,8.759,2.828z"
                    ></path>
                    <path
                      fill="none"
                      d="M1.238,7.171c0.027,0.047,0.077,0.074,0.128,0.074c0.025,0,0.051-0.008,0.074-0.02l1.211-0.699c0.071-0.041,0.095-0.133,0.054-0.203S2.574,6.228,2.503,6.269l-1.21,0.699C1.221,7.009,1.197,7.101,1.238,7.171z"
                    ></path>
                    <path
                      fill="none"
                      d="M6.396,2.726c0.052,0,0.102-0.026,0.13-0.075l0.349-0.605C6.915,1.976,6.89,1.885,6.819,1.844c-0.07-0.042-0.162-0.017-0.202,0.054L6.269,2.503C6.228,2.574,6.251,2.666,6.322,2.706C6.346,2.719,6.371,2.726,6.396,2.726z"
                    ></path>
                    <path
                      fill="none"
                      d="M3.472,7.347L3.123,7.952c-0.041,0.07-0.017,0.162,0.054,0.203C3.2,8.169,3.226,8.175,3.25,8.175c0.052,0,0.102-0.027,0.129-0.074l0.349-0.605c0.041-0.07,0.017-0.16-0.054-0.203C3.603,7.251,3.513,7.276,3.472,7.347z"
                    ></path>
                    <path
                      fill="none"
                      d="M3.601,2.726c0.025,0,0.051-0.007,0.074-0.02C3.746,2.666,3.77,2.574,3.729,2.503l-0.35-0.604C3.338,1.828,3.248,1.804,3.177,1.844C3.106,1.886,3.082,1.976,3.123,2.047l0.35,0.604C3.5,2.7,3.549,2.726,3.601,2.726z"
                    ></path>
                    <path
                      fill="none"
                      d="M6.321,7.292c-0.07,0.043-0.094,0.133-0.054,0.203l0.351,0.605c0.026,0.047,0.076,0.074,0.127,0.074c0.025,0,0.051-0.006,0.074-0.02c0.072-0.041,0.096-0.133,0.055-0.203l-0.35-0.605C6.483,7.276,6.393,7.253,6.321,7.292z"
                    ></path>
                    <path
                      fill="none"
                      d="M2.202,5.146c0.082,0,0.149-0.065,0.149-0.147S2.284,4.851,2.202,4.851H1.503c-0.082,0-0.148,0.066-0.148,0.148s0.066,0.147,0.148,0.147H2.202z"
                    ></path>
                    <path
                      fill="none"
                      d="M8.493,4.851H7.794c-0.082,0-0.148,0.066-0.148,0.148s0.066,0.147,0.148,0.147l0,0h0.699c0.082,0,0.148-0.065,0.148-0.147S8.575,4.851,8.493,4.851L8.493,4.851z"
                    ></path>
                    <path
                      fill="none"
                      d="M5.146,2.203V0.805c0-0.082-0.066-0.148-0.148-0.148c-0.082,0-0.148,0.066-0.148,0.148v1.398c0,0.082,0.066,0.149,0.148,0.149C5.08,2.352,5.146,2.285,5.146,2.203z"
                    ></path>
                    <path
                      fill="none"
                      d="M4.85,7.796v1.396c0,0.082,0.066,0.15,0.148,0.15c0.082,0,0.148-0.068,0.148-0.15V7.796c0-0.082-0.066-0.148-0.148-0.148C4.917,7.647,4.85,7.714,4.85,7.796z"
                    ></path>
                    <path
                      fill="none"
                      d="M2.651,3.473L1.44,2.774C1.369,2.732,1.279,2.757,1.238,2.828C1.197,2.899,1.221,2.989,1.292,3.031l1.21,0.699c0.023,0.013,0.049,0.02,0.074,0.02c0.051,0,0.101-0.026,0.129-0.075C2.747,3.604,2.722,3.514,2.651,3.473z"
                    ></path>
                    <path
                      fill="none"
                      d="M8.704,6.968L7.493,6.269c-0.07-0.041-0.162-0.016-0.201,0.055c-0.041,0.07-0.018,0.162,0.053,0.203l1.211,0.699c0.023,0.012,0.049,0.02,0.074,0.02c0.051,0,0.102-0.027,0.129-0.074C8.8,7.101,8.776,7.009,8.704,6.968z"
                    ></path>
                  </g>
                </svg>

                <svg
                  version="1.1"
                  id="cloud"
                  xmlns="http://www.w3.org/2000/svg"
                  xmlns:xlink="http://www.w3.org/1999/xlink"
                  x="0px"
                  y="0px"
                  width="10px"
                  height="10px"
                  viewBox="0 0 10 10"
                  enable-background="new 0 0 10 10"
                  xml:space="preserve"
                >
                  <path
                    fill="none"
                    d="M8.528,5.624H8.247c-0.085,0-0.156-0.068-0.156-0.154c0-0.694-0.563-1.257-1.257-1.257c-0.098,0-0.197,0.013-0.3,0.038C6.493,4.259,6.45,4.252,6.415,4.229C6.38,4.208,6.356,4.172,6.348,4.131C6.117,3.032,5.135,2.235,4.01,2.235c-1.252,0-2.297,0.979-2.379,2.23c-0.004,0.056-0.039,0.108-0.093,0.13C1.076,4.793,0.776,5.249,0.776,5.752c0,0.693,0.564,1.257,1.257,1.257h6.495c0.383,0,0.695-0.31,0.695-0.692S8.911,5.624,8.528,5.624z"
                  ></path>
                </svg>

                <div class="rain">
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                  <span class="drop"></span>
                </div>

                <div class="text">LOOKING OUTSIDE FOR YOU... ONE SEC</div>
              </div>
              <!-- loader end -->
            </div>
          </div>
        </div>

        <!-- forecaste cart area end  -->
        <!-- </slide> -->
      </div>
    </div>


  </section>

 
</template>

<script>
import axios from "axios";
import { Carousel, Slide } from "../node_modules/vue-carousel";
import { h } from "vue";

// var lat = "40.25631";
// var lon = "40.22289";
let lat = "40.25631";
let lon = "40.22289";
const CURRENTWEATHERAPI = `https://cors-anywhere.herokuapp.com/http://api.openweathermap.org/data/2.5/weather?lat={0}&lon={1}&appid=${process.env.VUE_APP_API_OMAP_KEY}`;
const FORECASTFIVEDAYAPI = `https://api.openweathermap.org/data/2.5/forecast?lat={0}&lon={1}&appid=${process.env.VUE_APP_API_OMAP_KEY}`;

const toDegree = -272.15;
console.log(typeof date);

// console.log(APIURL);

export default {
  components: {
    Carousel,
    Slide,
  },
  mounted() {
    this.getCurrentLocation();
  },
  data() {
    return {
      data: {},
      forecasteData: [],
      images: [
        {
          url: "https://bmcdn.nl/assets/weather-icons/v3.0/fill/svg/cloudy.svg",
          alt: "Clouds",
        },
        {
          url: "https://bmcdn.nl/assets/weather-icons/v3.0/fill/svg/clear-day.svg",
          alt: "Clear",
        },
        {
          url: "https://bmcdn.nl/assets/weather-icons/v3.0/fill/svg/overcast-rain.svg",
          alt: "Rain",
        },
        {
          url: "https://bmcdn.nl/assets/weather-icons/v3.0/fill/svg/snow.svg",
          alt: "Snow",
        },
      ],
    };
  },

  methods: {
    getCurrentLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(
          (position) => this.getPosition(position),
          (error) => console.error(error)
        );
      }
    },
    getPosition(position) {
      console.log(this);
      let lat = position.coords.latitude;
      let lon = position.coords.longitude;

      axios
        .get(
          `https://cors-anywhere.herokuapp.com/http://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&appid=b7c149aef4d068eccf67d83126ebbf26`
        )
        .then((res) => {
          console.error(res.data);
          this.data = res.data;
        });

      axios
        .get(
          `https://cors-anywhere.herokuapp.com/http://api.openweathermap.org/data/2.5/forecast?lat=${lat}&lon=${lon}&appid=b7c149aef4d068eccf67d83126ebbf26`
        )
        .then((res) => {
          console.error(res.data);
          const watherList = {};
          res.data.list.forEach((day) => {
            const [date] = day.dt_txt.split(" ");
            if (!watherList[date]) watherList[date] = day;
          });
          res.data.list.map((weather) => {
            console.log(
              weather.weather.map((item) => {
                console.log(item.main);
              })
            );
          });

          this.forecasteData = Object.values(watherList);
        });
    },
    setData(data) {
      this.data = data;
    },

    currentDate() {
      const current = new Date();
      console.log(current);
      const date = `${current.getDate()}/${current.getMonth() + 1}/${
        current.getFullYear() +
        "," +
        current.getHours() +
        ":" +
        current.getUTCMinutes()
      }`;
      return date;
    },
    // forecasteFiveDay() {
    //   axios.get(FORECASTFIVEDAYAPI).then((res) => {
    //     console.error(res.data.list);
    //   });
    // },
  },
};
</script>
