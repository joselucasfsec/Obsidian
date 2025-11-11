Tags: #web #xml

XML ou Extensible Markup Language é uma linguagem de marcação usada para codificar documentos de forma leível por humanos e máquinas é utilizada para amazenar dados. 
É amplamente utilizado para estruturar dados de forma hierárquica, permitindo que sejam facilmente lidos e compreendidos por diferentes softwares e sistemas

Por exemplo, considere um documento de texto com a extensão .xml contendo comentários. Esses comentários podem oferecer sugestões como estas:

- Deixar o título em negrito
- Esta frase é um cabeçalho
- Esta palavra é o autor

Esses comentários melhoram a praticidade do documento sem afetar seu conteúdo. Da mesma forma, o XML usa símbolos de marcação para fornecer mais informações sobre quaisquer dados. Outros softwares, como navegadores e aplicações de processamento de dados, usam essas informações para processar dados estruturados com mais eficiência.

### **Marcas XML**

Você usa símbolos de marcação, chamados de etiquetas em XML, para definir dados. Por exemplo, para representar dados de uma livraria, você pode criar etiquetas como ```<book>, <title> e <author>```. Seu documento XML para um único livro teria um conteúdo como este:
```
<book>
<title> Learning Amazon Web Services </title>
<author> Mark Wilkins </author>
</book>
```
Etiquetas trazem codificação de dados sofisticada para integrar fluxos de informações em diferentes sistemas.

O xml começa com uma tag raiz que delimita os dados do arquivo xml.
```
<?xml version="1.0">
<raiz>
</raiz?>
```
### Entidades
Em XML, entidades são usadas para representar caracteres ou grupos de caracteres que podem ser difíceis ou impossíveis de serem inseridos diretamente no texto, ou para referenciar conteúdo externo.
**Sintaxe para declaração de entidades:**
```
<!ENTITY nome_da_entidade "valor_da_entidade">
```

Por exemplo, para declarar uma entidade chamada "company" com o valor "Minha Empresa":
```
<!ENTITY company "Minha Empresa">
```

E para usar essa entidade em algum lugar do documento XML:
```
<nome>&company;</nome>
```

### Tipos de entidades XML:

- **Entidades internas:**
    
    São definidas dentro do próprio documento XML, geralmente em uma seção de declaração de entidade.
    
- **Entidades externas:**
    
    São definidas em arquivos separados e referenciadas no documento XML, muitas vezes através de um DTD

