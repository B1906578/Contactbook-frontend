<template>
    <div class="page">
        <h4>Thêm Liên hệ</h4>
        <form>
            <div class="form-group">
                <label for="name">Tên</label>
                <input name="name" type="text" class="form-control" v-model="contact.name" />
            </div>
            <div class="form-group">
                <label for="email">E-mail</label>
                <input name="email" type="email" class="form-control" v-model="contact.email" />
            </div>
            <div class="form-group">
                <label for="address">Địa chỉ</label>
                <input name="address" type="text" class="form-control" v-model="contact.address" />
            </div>
            <div class="form-group">
                <label for="phone">Điện thoại</label>
                <input name="phone" type="tel" class="form-control" v-model="contact.phone" />
            </div>
            <div class="form-group form-check">
                <input
                    name="favorite"
                    type="checkbox"
                    class="form-check-input"
                    v-model="contact.favorite"
                />
                <label for="favorite" class="form-check-label">
                    <strong>Liên hệ yêu thích</strong>
                </label>
            </div>
            <div class="form-group">
                <button class="btn btn-primary" @click="createContact">Lưu</button>
            </div>
        </form>
    </div>
</template>

<script>
import ContactService from "@/services/contact.service";

export default {
    data() {
        return {
            contact: { name: '', email: '', address: '', phone: '', favorite: '' },
        };
    },
    methods: {
        createContact() {
            let newContact = {
                name: this.contact.name,
                email: this.contact.email,
                address: this.contact.address,
                phone: this.contact.phone,
                favorite: this.contact.favorite
            }
            try {
                ContactService.create(newContact);
                confirm("Thêm liên hệ thành công.");
            } catch (error) {
                console.log(error);
            }
        },
    },
};
</script>

<style scoped>
@import "@/assets/form.css";
</style>