<template>
  <div class="flex p-3 border-">
    <Panel header="Yeni Sayfa Oluştur" class="w-full">
      <div class="grid grid-cols-12 gap-4">
        <div class="col-span-9">
          <div class="grid grid-cols-2 mb-4 gap-4">
            <div class="">
              <label for="Sayfa Başlığı"></label>
              <FloatLabel variant="in">
                <InputText v-model="page_title" class="w-full" />
                <label>Sayfa Başlığı</label>
              </FloatLabel>
            </div>
            <div class="">
              <FloatLabel variant="in">
                <Select
                  v-model="selected_city"
                  :options="cities"
                  optionLabel="name"
                  checkmark
                  :highlightOnSelect="false"
                  class="w-full"
                />
                <label>Sayfa Kategorisi</label>
              </FloatLabel>
            </div>
          </div>
          <div class="">
            <Editor
              v-model="page_content"
              editorStyle="height: 320px"
              class="w-full"
              placeholder="Sayfanın İçeriği"
            />
          </div>
        </div>
        <div class="col-span-3">
          <div
            class="space-y-8 p-3 lg:p-6 bg-gray-50 rounded-lg border shadow-sm"
          >
            <div>
              <Button size="medium" label="Yayınla" class="w-full mb-4" />
              <h4 class="font-semibold mb-4">SEO Ayarları</h4>
              <FloatLabel variant="in">
                <Textarea
                  id="over_label"
                  v-model="page_description"
                  rows="5"
                  class="w-full"
                  style="resize: none"
                />
                <label for="on_label">Sayfa Meta Açıklaması</label>
              </FloatLabel>
            </div>
            <div>
              <h4 class="font-semibold mb-4">Sayfa Görseli (Opsiyonel)</h4>
              <div>
                <div class="flex">
                  <FileUpload
                    mode="basic"
                    @select="onFileSelect"
                    customUpload
                    auto
                    severity="secondary"
                    class="p-button-outlined"
                  />
                </div>
                <img
                  v-if="page_img"
                  :src="page_img"
                  alt="Image"
                  class="shadow-md rounded-xl w-full sm:w-64"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </Panel>
  </div>
</template>

<script setup>
definePageMeta({
  layout: "admin",
});

const selected_city = ref();
const cities = ref([
  { name: "Kurumsal", id: "1" },
  { name: "Hukuki Metinler", id: "2" },
]);
const page_title = ref(null);
const page_content = ref(null);
const page_description = ref(null);
const page_img = ref(null);

function onFileSelect(event) {
  const file = event.files[0];
  const reader = new FileReader();

  reader.onload = async (e) => {
    page_img.value = e.target.result;
  };

  reader.readAsDataURL(file);
}
</script>
