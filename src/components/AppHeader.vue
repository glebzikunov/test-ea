<template>
  <header class="header">
    <div class="header__slate-left">
      <img src="../assets/blue-slate.svg" alt="Left Slate" />
    </div>
    <a class="header__logo" href="https://leadadvisors.org" target="_blank">
      <img src="../assets/logo.svg" alt="LeadAdvisors logo" />
    </a>
    <div class="header__slate-right">
      <img src="../assets/blue-slate.svg" alt="Right Slate" />
    </div>
  </header>
</template>

<style lang="scss" scoped>
.header {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: end;
  height: 171px;
}

.header__slate-left {
  position: absolute;
  top: -317.05px;
  left: -431.6px;
  z-index: 1;
  transform: rotate(-24deg);

  img {
    max-width: 100%;
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -o-user-select: none;
    user-select: none;
  }
}

.header__logo {
  position: relative;
  z-index: 20;

  img {
    max-width: 100%;
  }
}

.header__slate-right {
  position: absolute;
  top: -475.32px;
  right: -531.29px;
  z-index: 0;
  transform: rotate(-77.43deg);
  img {
    max-width: 100%;
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -o-user-select: none;
    user-select: none;
  }
}

@media (max-width: 767.98px) {
  .header__slate-left {
    width: 478px;
    height: 394px;
    top: -196.82px;
    left: -249.54px;
    transform: rotate(-24deg);
  }

  .header__slate-right {
    top: -500.74px;
    right: -514.29px;
    transform: rotate(-86.33deg);
  }
}

@media (max-width: 360px) {
  .header__slate-left {
    width: 366px;
    height: 302px;
    top: -165.38px;
    left: -200.24px;
    transform: rotate(-24deg);
  }

  .header__logo {
    width: 128px;
  }

  .header__slate-right {
    width: 642px;
    height: 530px;
    top: -376.08px;
    right: -407.53px;
    transform: rotate(-84.96deg);
  }
}
</style>
