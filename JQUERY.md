## JQUERY ##


### Masks ###
```javascript
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery.mask/1.14.15/jquery.mask.min.js"></script>
```

```javascript
<!-- MÁSCARAS -->
<script type="text/javascript" charset="utf-8">
    $(document).ready(function () {
        sliceValue("salario");
        sliceValue("gratificacao");
    });

    /**
     * Remove somente o último caractere da string e já atualiza o campo com o novo valor, para se adequar à máscara
     * @param element obrigatorio   ID do campo no qual deseja pegar a string
     *
     * @example
     *    "hello world" // "hello worl"
     */
    function sliceValue(element) {
        // Utilizar desta forma caso seja um campo do tipo 'form.text_field'
        // const elem = document.getElementById(element);
        // elem.value = elem.value.slice(0, -1)

        const elem = $('#' + element);
        elem.text(elem.text().slice(0, -1));
    }

    $(document).ready(function () {
        // 'reverse' aplica a máscara da direita pra esquerda, assim que começar a ser digitada. Somente necessário em campos editáveis, onde o usuário for escrever algo.
        // $('.cpf').mask('000.000.000-00', {reverse: true});
        $('.cpf').mask('000.000.000-00');
        $('.cep').mask('00000-000');
        $('.telefone_ddd').mask('(DD) C 0000-0000', {
            translation: {
                'D': {pattern: /[0-9]/, optional: true},
                'C': {pattern: /[9]/, optional: true}
            }
        });
        $('.cnpj').mask('00.000.000/0000-00', {reverse: true});
        $('.pis').mask('000.00000.00.0');
        $('.money').mask("#.##0,00", {reverse: true});
        $('.time').mask('AB:CD', {
            translation: {
                'A': {pattern: /[0-2]/, optional: false},
                'B': {pattern: /[0-9]/, optional: false},
                'C': {pattern: /[0-5]/, optional: false},
                'D': {pattern: /[0-9]/, optional: false}
            }
        });
        $('.ie').mask("00.000.000-0", {reverse: true});

    });
</script>
```

```html
<div class="row">
  <div class="col s12 m4">
    <label>Telefone:</label>
    <span class="telefone_ddd"><%= @arquivo_mestre.first[:telefone] %></span>
  </div>
</row>
```
