# Интерактивная консоль REST API

Раздел содержит OpenAPI-контракты для управления электроприводом затвора и сбора телеметрии.

<script src="https://unpkg.com/swagger-ui-dist@5/swagger-ui-bundle.js"></script>
<link rel="stylesheet" href="https://unpkg.com/swagger-ui-dist@5/swagger-ui.css" />

<div id="swagger-ui"></div>

<script>
window.onload = function() {
  SwaggerUIBundle({
    url: "../v1/valve-control.yaml",
    dom_id: "#swagger-ui",
  });
}
</script>