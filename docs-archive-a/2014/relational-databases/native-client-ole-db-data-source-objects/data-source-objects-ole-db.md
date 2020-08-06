---
title: 데이터 원본 개체(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cf3f0b0308d655b50149c174547c19966f550ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728228"
---
# <a name="data-source-objects-ole-db"></a><span data-ttu-id="b3297-102">데이터 원본 개체(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="b3297-102">Data Source Objects (OLE DB)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="b3297-103">Native Client는와 같은 데이터 저장소에 대 한 링크를 설정 하는 데 사용 되는 OLE DB 인터페이스 집합에 대해 데이터 원본 이라는 용어를 사용 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3297-103">Native Client uses the term data source for the set of OLE DB interfaces used to establish a link to a data store, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b3297-104">Native Client 소비자의 첫 번째 작업은 공급자의 데이터 원본 개체의 인스턴스를 만드는 것입니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b3297-104">Creating an instance of the data source object of the provider is the first task of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client consumer.</span></span>  
  
 <span data-ttu-id="b3297-105">각 OLE DB 공급자는 자체적으로 사용할 CLSID(클래스 식별자)를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="b3297-105">Every OLE DB provider declares a class identifier (CLSID) for itself.</span></span> <span data-ttu-id="b3297-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자의 CLSID는 C/c + + GUID CLSID_SQLNCLI10입니다. 기호 SQLNCLI_CLSID은 사용자가 참조 하는 SQLNCLI 파일의 올바른 progid로 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3297-106">The CLSID for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider is the C/C++ GUID CLSID_SQLNCLI10 (the symbol SQLNCLI_CLSID will resolve to the correct progid in the sqlncli.h file that you reference).</span></span> <span data-ttu-id="b3297-107">CLSID가 있으면 소비자는 OLE **CoCreateInstance** 함수를 사용하여 데이터 원본 개체의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3297-107">With the CLSID, the consumer uses the OLE **CoCreateInstance** function to manufacture an instance of the data source object.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="b3297-108">Native Client는 in-process 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="b3297-108">Native Client is an in-process server.</span></span> <span data-ttu-id="b3297-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 개체의 인스턴스는 CLSCTX_INPROC_SERVER 매크로를 사용 하 여 실행 컨텍스트를 나타내는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3297-109">Instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider objects are created using the CLSCTX_INPROC_SERVER macro to indicate the executable context.</span></span>  
  
 <span data-ttu-id="b3297-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 데이터 원본 개체는 소비자가 기존 데이터베이스에 연결할 수 있도록 하는 OLE DB 초기화 인터페이스를 제공 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b3297-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source object exposes the OLE DB initialization interfaces that allow the consumer to connect to existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="b3297-111">Native Client OLE DB 공급자를 통해 수행 된 모든 연결은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 자동으로 다음 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3297-111">Every connection made through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider sets these options automatically:</span></span>  
  
-   <span data-ttu-id="b3297-112">SET ANSI_WARNINGS ON</span><span class="sxs-lookup"><span data-stu-id="b3297-112">SET ANSI_WARNINGS ON</span></span>  
  
-   <span data-ttu-id="b3297-113">SET ANSI_NULLS ON</span><span class="sxs-lookup"><span data-stu-id="b3297-113">SET ANSI_NULLS ON</span></span>  
  
-   <span data-ttu-id="b3297-114">SET ANSI_PADDING ON</span><span class="sxs-lookup"><span data-stu-id="b3297-114">SET ANSI_PADDING ON</span></span>  
  
-   <span data-ttu-id="b3297-115">SET ANSI_NULL_DFLT_ON ON</span><span class="sxs-lookup"><span data-stu-id="b3297-115">SET ANSI_NULL_DFLT_ON ON</span></span>  
  
-   <span data-ttu-id="b3297-116">SET QUOTED_IDENTIFIER ON</span><span class="sxs-lookup"><span data-stu-id="b3297-116">SET QUOTED_IDENTIFIER ON</span></span>  
  
-   <span data-ttu-id="b3297-117">SET CONCAT_OF_NULL_YIELDS_NULL ON</span><span class="sxs-lookup"><span data-stu-id="b3297-117">SET CONCAT_OF_NULL_YIELDS_NULL ON</span></span>  
  
 <span data-ttu-id="b3297-118">이 예제에서는 클래스 식별자 매크로를 사용 하 여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 데이터 원본 개체를 만들고 해당 **IDBInitialize** 인터페이스에 대 한 참조를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b3297-118">This example uses the class identifier macro to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source object and get a reference to its **IDBInitialize** interface.</span></span>  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 <span data-ttu-id="b3297-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 데이터 원본 개체의 인스턴스를 성공적으로 만든 후에는 데이터 원본을 초기화 하 고 세션을 만들어 소비자 응용 프로그램을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3297-119">With successful creation of an instance of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source object, the consumer application can continue by initializing the data source and creating sessions.</span></span> <span data-ttu-id="b3297-120">OLE DB 세션은 데이터 액세스 및 조작을 가능하게 하는 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3297-120">OLE DB sessions present the interfaces that allow data access and manipulation.</span></span>  
  
 <span data-ttu-id="b3297-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 데이터 원본 초기화를 성공적으로 수행 하는 과정에서 지정 된 인스턴스에 대 한 첫 번째 연결을 만듭니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b3297-121">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider makes its first connection to a specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as part of a successful data source initialization.</span></span> <span data-ttu-id="b3297-122">이 연결은 데이터 원본 초기화 인터페이스에 대한 참조가 유지되는 동안이나 **IDBInitialize::Uninitialize** 메서드가 호출될 때까지 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3297-122">The connection is maintained as long as a reference is maintained on any data source initialization interface, or until the **IDBInitialize::Uninitialize** method is called.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3297-123">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="b3297-123">In This Section</span></span>  
  
-   [<span data-ttu-id="b3297-124">데이터 원본 속성&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="b3297-124">Data Source Properties &#40;OLE DB&#41;</span></span>](data-source-properties-ole-db.md)  
  
-   [<span data-ttu-id="b3297-125">데이터 원본 정보 속성</span><span class="sxs-lookup"><span data-stu-id="b3297-125">Data Source Information Properties</span></span>](data-source-information-properties.md)  
  
-   [<span data-ttu-id="b3297-126">초기화 및 권한 부여 속성</span><span class="sxs-lookup"><span data-stu-id="b3297-126">Initialization and Authorization Properties</span></span>](initialization-and-authorization-properties.md)  
  
-   [<span data-ttu-id="b3297-127">세션</span><span class="sxs-lookup"><span data-stu-id="b3297-127">Sessions</span></span>](sessions.md)  
  
-   [<span data-ttu-id="b3297-128">세션 속성</span><span class="sxs-lookup"><span data-stu-id="b3297-128">Session Properties</span></span>](session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [<span data-ttu-id="b3297-129">지속형 데이터 원본 개체</span><span class="sxs-lookup"><span data-stu-id="b3297-129">Persisted Data Source Objects</span></span>](persisted-data-source-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="b3297-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3297-130">See Also</span></span>  
 [<span data-ttu-id="b3297-131">SQL Server Native Client&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="b3297-131">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
