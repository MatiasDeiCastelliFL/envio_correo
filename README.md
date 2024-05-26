const nodemailer =require("nodemailer");

constconfig=(user_nodemailer, pass_nodemailer)=>{

  return nodemailer.createTransport({

    host:"smtp.gmail.com",

    port:465,

    secure:true,

    auth:{

    user: user_nodemailer,

    pass: pass_nodemailer,

    },

  });

};

functionenviar_email(

  config_user_nodemailer,

  config_pass_nodemailer,

  link_redirect,

  cuerpo_mensaje_subject,

  notificacion_razon,

  notificacion_titulo,

  notificacion_mensaje,

  boton_mensaje,

  email_recibe,

  enviar_logo,

  mensaje_accion

){

  let mensaje_html =``<!DOCTYPE html>`

    `<html lang="en">`

    `<head>`

    `<meta charset="UTF-8" />`

    `<meta http-equiv="X-UA-Compatible" content="IE=edge" />`

    `<meta name="viewport" content="width=device-width, initial-scale=1.0" />`

    `<style>`

    p,

    a,

    h1,

    h2,

    h3,

    h4,

    h5,

    h6 {

    font-family: "Roboto", sans-serif !important;

    }

    h1 {

    font-size: 30px !important;

    }

    h2 {

    font-size: 25px !important;

    }

    h3 {

    font-size: 18px !important;

    }

    h4 {

    font-size: 16px !important;

    }

    p,

    a {

    font-size: 15px !important;

    }

    .claseBoton {

    width: 30%;

    background-color: #fcae3b;

    border: 2px solid #fcae3b;

    color: black;

    padding: 16px 32px;

    text-align: center;

    text-decoration: none;

    font-weight: bold;

    display: inline-block;

    font-size: 16px;

    margin: 4px 2px;

    transition-duration: 0.4s;

    cursor: pointer;

    }

    .claseBoton:hover {

    background-color: #000000;

    color: #ffffff;

    }

    .imag {

    width: 20px;

    height: 20px;

    }

    .contA {

    margin: 0px 5px 0 5px;

    }

    .afooter {

    color: #ffffff !important;

    text-decoration: none;

    font-size: 13px !important;

    }

    `</style>`

    `</head>`

    `<body>`

    `<div style="width: 100%; background-color: #e3e3e3">`

    `<div style="padding: 20px 10px 20px 10px">`

    `<!-- Imagen inicial -->`

    <div

    style="

    background-color: #000000;

    padding: 10px 0px 10px 0px;

    width: 100%;

    text-align: center;

    "

    >

    <img

    src=${enviar_logo}

    alt="Error imagen"

    style="width: 200px; height: 60px"

    />

    `</div>`

    `<!-- Imagen inicial -->`

    `<!-- Contenido principal -->`

    <div

    style="

    background-color: #ffffff;

    padding: 20px 0px 5px 0px;

    width: 100%;

    text-align: center;

    "

    >

    `<h1>`${notificacion_titulo}`</h1>`

    `<p>`

    ${notificacion_mensaje}

    `</p>`

    `<!-- Gracias -->`

    `<p>`Gracias por tu tiempo.`</p>`

    `<p style="margin-bottom: 50px">`

    `<i>`Atentamente:`</i><br />`${mensaje_accion}

    `</p>`

    `<!-- Botón -->`

    `<a class="claseBoton" href=${link_redirect}>`${boton_mensaje}`</a>`

    `</div>`

    `<!-- Contenido principal -->`

    `<!-- Footer -->`

    <div

    style="

    background-color: #282828;

    color: #ffffff;

    padding: 5px 0px 0px 0px;

    width: 100%;

    text-align: center;

    "

    >

    <p

    style="

    background-color: black;

    padding: 10px 0px 10px 0px;

    font-size: 12px !important;

    "

    >

    © 2024 Activa Gym, todos los derechos reservados.

    `</p>`

    `</div>`

    `<!-- Footer -->`

    `</div>`

    `</div>`

    `</body>`

    `</html>``;

  const transporter =config(config_user_nodemailer, config_pass_nodemailer);

  transporter

    .verify()

    .then(()=>{

    console.log("Conexion establecida correctamente");

    })

    .catch((err)=>console.log(err));

  transporter

    .sendMail({

    from:`Activa Gym: ${config_user_nodemailer}`,

    to: email_recibe,

    subject: cuerpo_mensaje_subject,

    text: notificacion_razon,

    html: mensaje_html,

    })

    .then((info)=>{

    console.log(info);

    })

    .catch((error)=>{

    console.log(error);

    });

}

module.exports={ enviar_email };
