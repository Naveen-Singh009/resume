<binding name="PortTypeBinding" type="tns:PortType">
    ...
</binding>

<service name="FraudService">
    <port name="FraudPort" binding="tns:PortTypeBinding">
        <soap:address location="http://localhost:8080/FraudService"/>
    </port>
</service>