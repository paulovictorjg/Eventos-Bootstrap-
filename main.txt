$(document).ready(function(){

    $('#phone').mask('(00) 00000-0000');

    $('#contactForm').on('submit', function(event) {
        event.preventDefault();

        const name = $('#name').val();
        const email = $('#email').val();
        const phone = $('#phone').val();
        const eventDate = $('#eventDate').val();
        const message = $('#message').val();

        let isValid = true;
        const responseDiv = $('#form-response');

        responseDiv.removeClass('alert alert-success alert-danger').addClass('d-none').text('');
        $('input, textarea').removeClass('is-invalid');

        if (name.trim() === '') {
            $('#name').addClass('is-invalid');
            isValid = false;
        }

        if (email.trim() === '' || !/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
            $('#email').addClass('is-invalid');
            isValid = false;
        }

        if (phone.trim() === '' || phone.length < 15) { // (00) 00000-0000 tem 15 caracteres
            $('#phone').addClass('is-invalid');
            isValid = false;
        }

        if (eventDate.trim() === '') {
            $('#eventDate').addClass('is-invalid');
            isValid = false;
        }

        if (message.trim() === '') {
            $('#message').addClass('is-invalid');
            isValid = false;
        }

        if (isValid) {
        // adicionar futuramente oara o meu servidor de dados ou nuvem    

            responseDiv.text('Formulário enviado com sucesso! Em breve entraremos em contato.').removeClass('d-none').addClass('alert alert-success');
            $('#contactForm')[0].reset();
            $('input, textarea').removeClass('is-invalid');
        } else {
            responseDiv.text('Por favor, preencha todos os campos obrigatórios corretamente.').removeClass('d-none').addClass('alert alert-danger');
        }
    });

});
