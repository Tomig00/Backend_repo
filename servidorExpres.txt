const fs = require("fs")
const { resolve } = require("path/posix")


const express = require('express')
const app = express()

const PORT = 8080

const conectedserver = app.listen(PORT, () => {
    console.log(`iniciado en el puerto ${conectedserver.address().port}`)
})

app.get('/productos', (req, res) => {
    const test = new Contenedor()
    productos = JSON.stringify(test.getAll())
    res.end(`<h1 style = 'color:blue;'> ARRAY DE PRODUCTOS</h1>${productos}`)
    //res.json(test.getAll())
})

app.get('/productoRandom', (req, res) => {
    const test = new Contenedor()
    producto = JSON.stringify(test.getAleatorio())
    res.end(`<h1 style = 'color:green;'> PRODUCTO ALEATORIO</h1>${producto}`)
})


class Contenedor{
    getAll()
    {
        let arregloOld = []
        
        arregloOld = JSON.parse(fs.readFileSync("./productos.txt", "utf-8"))
        console.log(arregloOld)
        return arregloOld
    }

    getAleatorio()
    {
        let arregloOld = []
        let objeto
        
        arregloOld = JSON.parse(fs.readFileSync("./productos.txt", "utf-8"))

        let id = idAleatorio(0, arregloOld.length)

        objeto = arregloOld[id]
        console.log(objeto)
        return objeto
    }
}

function idAleatorio(min, max)
{
    return Math.floor(Math.random() * (max - min)) + min;
}

