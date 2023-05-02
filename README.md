# usingClassInMainwindow
#include "mainwindow.h"
#include "ui_mainwindow.h"
#include "testingshowsomething.h"
#include<QMessageBox>
MainWindow::MainWindow(QWidget *parent)
    : QMainWindow(parent)
    , ui(new Ui::MainWindow)
{
    ui->setupUi(this);
}

MainWindow::~MainWindow()
{
    delete ui;
}


void MainWindow::on_show_clicked()
{
    testingShowSomething obj1;
    int age = obj1.calculateAge(ui->yearLine->text());
    QString message = "Your age is " + QString::number(age);
    QMessageBox::information(this , tr("Announcing Age") , (message));
}
