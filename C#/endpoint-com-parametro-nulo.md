# Endpoint com Parâmetro Nulo

**Objetivo:** Configurar parâmetros de um endpoint para aceitar valores nulos.

## Etapa 1 - Criar um Endpoint

```
[HttpGet]
[Route("obter-cliente/{codCliente}")]       
public HttpResponseMessage ObterCliente(int codCliente)
{
    ServicoExternoQualquer servico = new ServicoExternoQualquer();
    var cliente = servico.ObterCliente(codCliente);

    if (cliente == null) return CreateResponse(HttpStatusCode.BadRequest, "Cliente não encontrado.");

    return CreateResponse(HttpStatusCode.OK, cliente);
}
```

## Etapa 2 - Adicionar os parâmetros com valor nulo como padrão

```
[HttpGet]
[Route("obter-cliente/{codCliente}")]       
public HttpResponseMessage ObterCliente(int? codCliente=null)
{
    ServicoExternoQualquer servico = new ServicoExternoQualquer();
    var cliente = servico.ObterCliente(codCliente);

    if (cliente == null) return CreateResponse(HttpStatusCode.BadRequest, "Cliente não encontrado.");

    return CreateResponse(HttpStatusCode.OK, cliente);
}
```

## Obs - Apenas indicar não é suficiente

```
[HttpGet]
[Route("obter-cliente/{codCliente}")]       
public HttpResponseMessage ObterCliente(int? codCliente)
{
    ServicoExternoQualquer servico = new ServicoExternoQualquer();
    var cliente = servico.ObterCliente(codCliente);

    if (cliente == null) return CreateResponse(HttpStatusCode.BadRequest, "Cliente não encontrado.");

    return CreateResponse(HttpStatusCode.OK, cliente);
}
```


