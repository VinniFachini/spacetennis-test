<template>
  <header>
    <div class="container">
      <div @click="toggleMobileMenu" class="mobile-menu" style="display: none">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          style="fill: rgba(0, 0, 0, 1); transform: ; msfilter: "
        >
          <path d="M4 6h16v2H4zm0 5h16v2H4zm0 5h16v2H4z"></path>
        </svg>
      </div>
      <div class="header-logo">
        <a href="/">
          <img class="logo" src="../static/assets/logo.svg" alt="" />
        </a>
      </div>
      <nav class="desktop">
        <span>Tipos de Calçado</span>
        <span>Marcas</span>
        <span>Gênero</span>
        <span>Tamanho Especial</span>
        <span>Opiniões</span>
        <span>Outlet</span>
      </nav>
      <nav :class="{ active }" class="mobile" style="display: none">
        <div class="background">
          <div>
            <span>Minha Conta</span>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              style="fill: #ccc; transform: ; msfilter: "
            >
              <path
                d="M10.707 17.707 16.414 12l-5.707-5.707-1.414 1.414L13.586 12l-4.293 4.293z"
              ></path>
            </svg>
          </div>
          <div>
            <span>Informações</span>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              style="fill: #ccc; transform: ; msfilter: "
            >
              <path
                d="M10.707 17.707 16.414 12l-5.707-5.707-1.414 1.414L13.586 12l-4.293 4.293z"
              ></path>
            </svg>
          </div>
          <div>
            <span>Tipos de Calçados</span>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              style="fill: #ccc; transform: ; msfilter: "
            >
              <path
                d="M10.707 17.707 16.414 12l-5.707-5.707-1.414 1.414L13.586 12l-4.293 4.293z"
              ></path>
            </svg>
          </div>
          <div>
            <span>Gênero</span>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              style="fill: #ccc; transform: ; msfilter: "
            >
              <path
                d="M10.707 17.707 16.414 12l-5.707-5.707-1.414 1.414L13.586 12l-4.293 4.293z"
              ></path>
            </svg>
          </div>
          <div><span>Tamanho Especial</span></div>
          <div><span>Opiniões</span></div>
          <div><span>Outlet</span></div>
        </div>
        <svg
        @click="toggleMobileMenu"
          class="active"
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          style="fill: rgba(255, 255, 255, 0.75); transform: ; msfilter: "
        >
          <path
            d="M13.293 6.293 7.586 12l5.707 5.707 1.414-1.414L10.414 12l4.293-4.293z"
          ></path>
        </svg>
      </nav>
      <div class="col3">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="21.811"
          height="20.385"
          viewBox="0 0 21.811 20.385"
        >
          <g id="search" transform="translate(0.75 0.75)">
            <g id="search_icon">
              <g id="Group_5513" data-name="Group 5513">
                <circle
                  id="Ellipse_5"
                  data-name="Ellipse 5"
                  cx="7.458"
                  cy="7.458"
                  r="7.458"
                  fill="none"
                  stroke="#000"
                  stroke-miterlimit="10"
                  stroke-width="1.5"
                />
                <line
                  id="Line_2"
                  data-name="Line 2"
                  x2="6.43"
                  y2="6.249"
                  transform="translate(13.57 12.325)"
                  fill="none"
                  stroke="#000"
                  stroke-linecap="round"
                  stroke-miterlimit="10"
                  stroke-width="1.5"
                />
              </g>
            </g>
          </g>
        </svg>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="34.08"
          height="21.196"
          viewBox="0 0 34.08 21.196"
        >
          <g
            id="Group_8404"
            data-name="Group 8404"
            transform="translate(-1212.268 -30)"
          >
            <line
              id="Line_1272"
              data-name="Line 1272"
              x2="4"
              y2="4"
              transform="translate(1237.5 39.5)"
              fill="none"
              stroke="#000"
              stroke-linecap="round"
              stroke-width="1.2"
            />
            <line
              id="Line_1273"
              data-name="Line 1273"
              x1="4"
              y2="4"
              transform="translate(1241.5 39.5)"
              fill="none"
              stroke="#000"
              stroke-linecap="round"
              stroke-width="1.2"
            />
            <g
              id="Ellipse_69"
              data-name="Ellipse 69"
              transform="translate(1217 30)"
              fill="#fff"
              stroke="#000"
              stroke-linecap="round"
              stroke-width="1.2"
            >
              <circle cx="6.5" cy="6.5" r="6.5" stroke="none" />
              <circle cx="6.5" cy="6.5" r="5.9" fill="none" />
            </g>
            <path
              id="Path_32503"
              data-name="Path 32503"
              d="M3521.079,136.6h21.079s-1.277-6.571-10.217-6.436S3521.079,136.6,3521.079,136.6Z"
              transform="translate(-2308 -86)"
              fill="none"
              stroke="#000"
              stroke-linecap="round"
              stroke-width="1.2"
            />
          </g>
        </svg>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="25.162"
          height="17.634"
          viewBox="0 0 25.162 17.634"
        >
          <g
            id="Group_8438"
            data-name="Group 8438"
            transform="translate(-1272.647 -32.366)"
          >
            <path
              id="Path_32502"
              data-name="Path 32502"
              d="M3581.248,118.966h23.833l-1.859,9.52h-13.23l-1.547-6.779"
              transform="translate(-2308 -86)"
              fill="none"
              stroke="#000"
              stroke-linecap="round"
              stroke-width="1.2"
            />
            <g
              id="Ellipse_67"
              data-name="Ellipse 67"
              transform="translate(1279 44)"
              fill="#fff"
              stroke="#000"
              stroke-linecap="round"
              stroke-width="1.2"
            >
              <circle cx="3" cy="3" r="3" stroke="none" />
              <circle cx="3" cy="3" r="2.4" fill="none" />
            </g>
            <g
              id="Ellipse_68"
              data-name="Ellipse 68"
              transform="translate(1290 44)"
              fill="#fff"
              stroke="#000"
              stroke-linecap="round"
              stroke-width="1.2"
            >
              <circle cx="3" cy="3" r="3" stroke="none" />
              <circle cx="3" cy="3" r="2.4" fill="none" />
            </g>
          </g>
        </svg>
      </div>
    </div>
    <div style="display: none" class="search-querry">
      <div class="form-group">
        <input type="text" placeholder="DIGITE O QUE PROCURA" />
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="21.811"
          height="20.385"
          viewBox="0 0 21.811 20.385"
        >
          <g id="search" transform="translate(0.75 0.75)">
            <g id="search_icon">
              <g id="Group_5513" data-name="Group 5513">
                <circle
                  id="Ellipse_5"
                  data-name="Ellipse 5"
                  cx="7.458"
                  cy="7.458"
                  r="7.458"
                  fill="none"
                  stroke="#000"
                  stroke-miterlimit="10"
                  stroke-width="1.5"
                />
                <line
                  id="Line_2"
                  data-name="Line 2"
                  x2="6.43"
                  y2="6.249"
                  transform="translate(13.57 12.325)"
                  fill="none"
                  stroke="#000"
                  stroke-linecap="round"
                  stroke-miterlimit="10"
                  stroke-width="1.5"
                />
              </g>
            </g>
          </g>
        </svg>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      name: 'Header',
      active: false,
    };
  },
  methods: {
    toggleMobileMenu: function () {
      this.active = !this.active
    },
  },
};
</script>

<style scoped>
header {
  width: 100vw;
  height: 95px;
  background-color: white;
  -webkit-box-shadow: 0 0 30px rgb(0 0 0 / 8%);
  box-shadow: 0 0 30px rgb(0 0 0 / 8%);
  display: flex;
  align-items: center;
  justify-content: center;
}

.container {
  width: 100%;
  max-width: 1260px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
}

.header-logo {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
}

.header-logo a {
  height: 100%;
}
.logo {
  width: 165px;
  height: 100%;
  max-height: 95px;
  transform: scale(1.25);
}

.container nav.desktop {
  display: flex;
  gap: 20px;
  margin-left: -250px;
}
.container nav.desktop span {
  display: inline-block;
  color: #003a77;
  text-transform: uppercase;
  font-weight: 600;
  font-size: 0.875em;
  cursor: pointer;
}

.mobile {
  transition: all .3s;
}

.logo {
  width: 165px;
  height: auto;
}

.col3 {
  display: flex;
  align-items: center;
  justify-content: space-around;
  gap: 40px;
}

@media screen and (max-width: 1366px) {
  .container {
    padding: 0 2%;
  }
  .container nav.desktop {
    margin-left: 0;
  }
  .col3 {
    display: flex;
    align-items: center;
    justify-content: space-around;
    gap: 20px;
  }
}

@keyframes animateEntry {
  from {
    opacity: 0;
    transform: translateX(-100vw);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes animateLeave {
  from {
    opacity: 1;
    transform: translateX(0);
  }
  to {
    opacity: 0;
    transform: translateX(-100vw);
  }
}

@media screen and (max-width: 991px) {
  header {
    border-bottom: 1px solid #ccc;
  }
  .container {
    padding: 0 8%;
  }
  .container .mobile-menu {
    display: flex !important;
  }

  .mobile > div.background{
    animation: animateLeave 0.5s;
  }

  .mobile.active {
    display: flex !important;
    background-color: rgba(0, 0, 0, 0.5);
    position: absolute;
    top: 0;
    right: 0;
    width: 100vw;
    height: 100vh;
    z-index: 10;
  }

  .mobile.active > svg {
    transform: scale(1.5);
    position: absolute;
    top: 48%;
    left: calc(70% + 10px);
  }

  .mobile.active > div.background {
    width: 70%;
    height: 100%;
    background-color: #fff;
    display: flex;
    flex-direction: column;
    animation: animateEntry 0.5s;
  }

  .mobile.active > div.background > div {
    display: flex;
    padding: 10px;
    height: 55px;
    border-bottom: 1px solid #ccc;
    justify-content: space-between;
    align-items: center;
  }

  .mobile.active > div.background > div > span {
    text-transform: uppercase;
    font-weight: 400;
    font-size: 13px;
    padding-left: 20px;
    letter-spacing: 0.075em;
    color: #080808;
  }

  .mobile.active > div.background > div:nth-of-type(3),
  .mobile.active > div.background > div:nth-of-type(4),
  .mobile.active > div.background > div:nth-of-type(5),
  .mobile.active > div.background > div:nth-of-type(6),
  .mobile.active > div.background > div:nth-of-type(7) {
    padding-left: 30px;
  }

  .mobile.active > div.background > div:nth-of-type(1),
  .mobile.active > div.background > div:nth-of-type(2) {
    background: #222;
  }
  .mobile.active > div.background > div:nth-of-type(1) > span,
  .mobile.active > div.background > div:nth-of-type(2) > span {
    color: white;
  }
  .mobile.active > div.background > div:nth-of-type(1) {
    border-bottom: 1px solid white;
  }

  .container nav.desktop {
    display: none;
  }
  .col3 svg:nth-of-type(1),
  .col3 svg:nth-of-type(2) {
    display: none;
  }
  .col3 svg:nth-of-type(3),
  .container .mobile-menu {
    transform: scale(1.25);
  }
  .search-querry {
    display: flex !important;
    position: absolute;
    top: 95px;
    width: 100%;
    background-color: white;
    height: 22px;
    border-bottom: 1px solid #ccc;
    padding: 15px;
  }

  .search-querry .form-group {
    display: flex;
    width: 100%;
    height: 100%;
    align-items: center;
    justify-content: space-between;
    margin: 0 2%;
  }
  .form-group input[type="text"] {
    all: unset;
    font-size: 0.875em;
  }
}
</style>