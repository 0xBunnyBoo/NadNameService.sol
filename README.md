interface INadNameService {
    struct Attribute {
        string key;
        string value;
    }

    /**
     * @notice Emitted when a name's attribute is set.
     * @param node the hash of the name that attribute was set for
     * @param key the key of the attribute that was set
     * @param value the value of the attribute that was set
     */
    event AttributeSet(bytes32 indexed node, string key, string value);

    /**
     * @notice Emitted when multiple attributes for a name are set.
     * @param node the hash of the name that attributes were set for
     * @param attributes an array of attributes with the keys and values
     */
    event AttributesSet(bytes32 indexed node, Attribute[] attributes);
    
    /**
     * @notice Get the resolved address for a name.
     * @param node the hash of the name to get the resolved address for
     * @return the resolved address
     */
    function getResolvedAddress(
       bytes32 node
    ) external view returns (address);
    
     /**
     * @notice Get the primary name for a node.
     * @param node The node address to get the primary name for
     * @return The primary name for the address
     */
    function getPrimaryNameForNode(
        bytes32 node
    ) external view returns (string memory);

    /**
     * @notice Get the primary name for an address.
     * @param addr The address to get the primary name for
     * @return The primary name for the address
     */
    function getPrimaryNameForAddress(
        address addr
    ) external view returns (string memory);
    
    /**
     * @notice Set an attribute for a name.
     * @param node the hash of the name to set the attribute for
     * @param key the key of the attribute to set
     * @param value the value of the attribute to set
     */
    function setNameAttribute(
        bytes32 node,
        string calldata key,
        string calldata value
    ) external;

    /**
     * @notice Set multiple attributes for a name.
     * @param node the hash of the name to set the attributes for
     * @param attributes an array of attributes with the keys and values
     */
    function setNameAttributes(
        bytes32 node,
        Attribute[] calldata attributes
    ) external;

    /**
     * @notice Get an attribute for a name.
     * @param node the hash of the name to get the attribute for
     * @param key the key of the attribute to get
     * @return result value of the attribute
     */
    function getNameAttribute(
        bytes32 node,
        string calldata key
    ) external view returns (string memory);

    /**
     * @notice Get multiple attributes for a name
     * @param node the hash of the name to get the attributes for
     * @param keys the keys of the attributes to get
     * @return result an array of attributes with the keys and values
     */
    function getNameAttributes(
        bytes32 node,
        string[] calldata keys
    ) external view returns (Attribute[] memory);
}
