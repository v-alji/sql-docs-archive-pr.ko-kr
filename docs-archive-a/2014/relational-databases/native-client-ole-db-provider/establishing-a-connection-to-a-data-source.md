---
title: 데이터 원본에 대한 연결 설정 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [SQL Server Native Client]
- connections [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, data source connections
- CoCreateInstance method
- OLE DB data sources [SQL Server Native Client]
ms.assetid: 7ebd1394-cc8d-4bcf-92f3-c374a26e7ba0
author: rothja
ms.author: jroth
ms.openlocfilehash: f88454339ee932c38655819cce475ab52d79975f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653831"
---
# <a name="establishing-a-connection-to-a-data-source"></a><span data-ttu-id="bf787-102">데이터 원본에 대한 연결 설정</span><span class="sxs-lookup"><span data-stu-id="bf787-102">Establishing a Connection to a Data Source</span></span>
  <span data-ttu-id="bf787-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자에 액세스 하려면 소비자는 먼저 **CoCreateInstance** 메서드를 호출 하 여 데이터 원본 개체의 인스턴스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-103">To access the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the consumer must first create an instance of a data source object by calling the **CoCreateInstance** method.</span></span> <span data-ttu-id="bf787-104">각 OLE DB 공급자는 고유한 CLSID(클래스 ID)를 사용하여 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-104">A unique class identifier (CLSID) identifies each OLE DB provider.</span></span> <span data-ttu-id="bf787-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자의 경우 클래스 식별자가 CLSID_SQLNCLI10 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-105">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the class identifier is CLSID_SQLNCLI10.</span></span> <span data-ttu-id="bf787-106">참조 하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLNCLI에서 사용 되는 Native Client OLE DB 공급자를 확인 하는 SQLNCLI_CLSID 기호를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-106">You can also use the symbol SQLNCLI_CLSID that will resolve to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider that is used in the sqlncli.h that you reference.</span></span>  
  
 <span data-ttu-id="bf787-107">소비자는 데이터 원본 개체가 공개하는 **IDBProperties** 인터페이스를 사용하여 서버 이름, 데이터베이스 이름, 사용자 ID 및 암호와 같은 기본 인증 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-107">The data source object exposes the **IDBProperties** interface, which the consumer uses to provide basic authentication information such as server name, database name, user ID, and password.</span></span> <span data-ttu-id="bf787-108">이러한 속성을 설정하려면 **IDBProperties::SetProperties** 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-108">The **IDBProperties::SetProperties** method is called to set these properties.</span></span>  
  
 <span data-ttu-id="bf787-109">컴퓨터에서 여러 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 실행되는 경우 서버 이름은 ServerName\InstanceName 형식으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-109">If there are multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the computer, the server name is specified as ServerName\InstanceName.</span></span>  
  
 <span data-ttu-id="bf787-110">데이터 원본 개체는 또한 **IDBInitialize** 인터페이스를 공개합니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-110">The data source object also exposes the **IDBInitialize** interface.</span></span> <span data-ttu-id="bf787-111">속성을 설정한 다음에는 **IDBInitialize::Initialize** 메서드를 호출하여 데이터 원본에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-111">After the properties are set, connection to the data source is established by calling the **IDBInitialize::Initialize** method.</span></span> <span data-ttu-id="bf787-112">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-112">For example:</span></span>  
  
```  
CoCreateInstance(CLSID_SQLNCLI10,   
                 NULL,   
                 CLSCTX_INPROC_SERVER,  
                 IID_IDBInitialize,   
                 (void **) &pIDBInitialize)  
```  
  
 <span data-ttu-id="bf787-113">이 **CoCreateInstance** 호출은 CLSID_SQLNCLI10와 연결 된 클래스의 단일 개체 (데이터와 연결 된 CSLID 개체를 만드는 데 사용 되는 코드)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-113">This call to **CoCreateInstance** creates a single object of the class associated with CLSID_SQLNCLI10 (CSLID associated with the data and code that will be used to create the object).</span></span> <span data-ttu-id="bf787-114">IID_IDBInitialize는 개체와 통신하는 데 사용되는 인터페이스(**IDBInitialize**)의 식별자에 대한 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-114">IID_IDBInitialize is a reference to the identifier of the interface (**IDBInitialize**) to be used to communicate with the object.</span></span>  
  
 <span data-ttu-id="bf787-115">다음 예제 함수는 데이터 원본에 대한 연결을 초기화하고 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf787-115">The following is a sample function that initializes and establishes a connection to the data source.</span></span>  
  
```  
void InitializeAndEstablishConnection() {  
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the SQL Server Native Client OLE DB provider.  
   hr = CoCreateInstance(CLSID_SQLNCLI10,   
                         NULL,   
                         CLSCTX_INPROC_SERVER,  
                         IID_IDBInitialize,   
                         (void **) &pIDBInitialize);  
   // Initialize property values needed to establish connection.  
   for (i = 0 ; i < 4 ; i++)   
      VariantInit(&InitProperties[i].vValue);  
  
   // Server name.  
   // See DBPROP structure for more information on InitProperties  
   InitProperties[0].dwPropertyID  = DBPROP_INIT_DATASOURCE;  
   InitProperties[0].vValue.vt    = VT_BSTR;  
   InitProperties[0].vValue.bstrVal=   
                     SysAllocString(L"Server");  
   InitProperties[0].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[0].colid       = DB_NULLID;  
  
   // Database.  
   InitProperties[1].dwPropertyID  = DBPROP_INIT_CATALOG;  
   InitProperties[1].vValue.vt    = VT_BSTR;  
   InitProperties[1].vValue.bstrVal= SysAllocString(L"database");  
   InitProperties[1].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[1].colid       = DB_NULLID;  
  
   // Username (login).  
   InitProperties[2].dwPropertyID  = DBPROP_AUTH_INTEGRATED;  
   InitProperties[2].vValue.vt    = VT_BSTR;  
   InitProperties[2].vValue.bstrVal= SysAllocString(L"SSPI");  
   InitProperties[2].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[2].colid       = DB_NULLID;  
   InitProperties[3].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[3].colid       = DB_NULLID;  
  
   // Construct the DBPROPSET structure(rgInitPropSet). The   
   // DBPROPSET structure is used to pass an array of DBPROP   
   // structures (InitProperties) to the SetProperties method.  
   rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties   = 4;  
   rgInitPropSet[0].rgProperties   = InitProperties;  
  
   // Set initialization properties.  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties,   
                           (void **)&pIDBProperties);  
   hr = pIDBProperties->SetProperties(1, rgInitPropSet);   
   pIDBProperties->Release();  
  
   // Now establish the connection to the data source.  
   pIDBInitialize->Initialize();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf787-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf787-116">See Also</span></span>  
 [<span data-ttu-id="bf787-117">SQL Server Native Client OLE DB 공급자 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="bf787-117">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
