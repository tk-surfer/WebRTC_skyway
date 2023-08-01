<script setup lang="js">
  import {computed, ref} from 'vue';
  const localVideo = ref(null);
  let localStream;


  const startVideo = () => {
    navigator.mediaDevices.getUserMedia({
      video: true,
      audio: false
      }).then(
        stream => (localVideo.value.srcObject = stream)
    ).catch(function (error) { // error
      console.error('mediaDevice.getUserMedia() error:', error);
      return;
    });
  };
  
  const stopVideo = () => {
    localVideo.value.srcObject.getTracks().forEach(function(track) {
      if (track.readyState == 'live') {
          track.stop();
      }
    });
  };

  // 通信処理

  // HTML要素の取得
  const buttonArea = document.getElementById('button-area');
  const remoteMediaArea = document.getElementById('remote-media-area');
  const roomNameInput = document.getElementById('room-name');
  const myId = document.getElementById('my-id');
  const joinButton = document.getElementById('join');

  /*
  // joinButtonが押された場合のイベントハンドラ
  joinButton.onclick = async () => {
    if (roomNameInput.value === '') return;

    // SkyWay Auth Tokenを用いて、contextを作成する
    // グローバルな情報を管理する
    const context = await SkyWayContext.Create(token);
  };*/

</script>

<template>
  <section class="hero is-primary">
    <div class="hero-body">
      <p class="title">
        Video
      </p>
      <p class="subtitle">
        接続しているカメラデバイスから映像を取得できます
      </p>
    </div>
  </section>

  <div class="has-text-centered">
    <video ref="localVideo" autoplay style="width:560px; height:400px; border:1px solid black;"></video>
    <br/>
    <button class="button is-centered is-primary"  @click="startVideo">start</button>
    <button class="button is-centered is-danger"  @click="stopVideo">stop</button>
  </div>
</template>

<style scoped>
.hero{
  margin-top: 10px;
}
.has-text-centered{
  margin: 10px;
}
</style>
