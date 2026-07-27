<binding name="PortTypeBinding" type="tns:PortType">
<definitions
    targetNamespace="http://xmlns.example.com/1785147428122"
    xmlns="http://schemas.xmlsoap.org/wsdl/"
    xmlns:tns="http://xmlns.example.com/1785147428122"
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/">


<?xml version="1.0" encoding="UTF-8"?>

<definitions
    name="FraudService"
    targetNamespace="http://xmlns.example.com/1785147428122"

    xmlns="http://schemas.xmlsoap.org/wsdl/"
    xmlns:tns="http://xmlns.example.com/1785147428122"
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
    xmlns:ns="http://www.tibco.com/schemas/newproject5/SharedResources/Schema/Schema.xsd">

    <types>
        <xsd:schema>
            <xsd:import
                namespace="http://www.tibco.com/schemas/newproject5/SharedResources/Schema/Schema.xsd"
                schemaLocation="../Schema/Schema.xsd"/>
        </xsd:schema>
    </types>

    <!-- Messages -->

    <message name="ValidUserRequest">
        <part name="parameters" element="ns:ValidUserRequest"/>
    </message>

    <message name="FraudCheckRequest">
        <part name="parameters" element="ns:FraudCheckRequest"/>
    </message>

    <message name="Response">
        <part name="parameters" element="ns:Response"/>
    </message>

    <!-- Port Type -->

    <portType name="PortType">

        <operation name="ValidateUser">
            <input message="tns:ValidUserRequest"/>
            <output message="tns:Response"/>
        </operation>

        <operation name="FraudCheck">
            <input message="tns:FraudCheckRequest"/>
            <output message="tns:Response"/>
        </operation>

    </portType>

    <!-- Binding -->

    <binding name="PortTypeBinding" type="tns:PortType">

        <soap:binding style="document"
                      transport="http://schemas.xmlsoap.org/soap/http"/>

        <operation name="ValidateUser">

            <soap:operation soapAction="ValidateUser"/>

            <input>
                <soap:body use="literal"/>
            </input>

            <output>
                <soap:body use="literal"/>
            </output>

        </operation>

        <operation name="FraudCheck">

            <soap:operation soapAction="FraudCheck"/>

            <input>
                <soap:body use="literal"/>
            </input>

            <output>
                <soap:body use="literal"/>
            </output>

        </operation>

    </binding>

    <!-- Service -->

    <service name="FraudService">

        <port name="FraudPort"
              binding="tns:PortTypeBinding">

            <soap:address
                location="http://localhost:8085/FraudService"/>

        </port>

    </service>

</definitions>