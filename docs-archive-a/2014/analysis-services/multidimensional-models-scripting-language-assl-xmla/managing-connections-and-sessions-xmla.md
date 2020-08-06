---
title: 연결 및 세션 관리 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- statefulness [XML for Analysis]
- statelessness [XML for Analysis]
- XML for Analysis, sessions
- states [XML for Analysis]
- XMLA, sessions
- sessions [XML for Analysis]
ms.assetid: b83bb3ff-09be-4fda-9d1d-6248e04ffb21
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7bfe876f6874193fd0885f16d91caa9f6fe8b172
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649765"
---
# <a name="managing-connections-and-sessions-xmla"></a><span data-ttu-id="b7b24-102">연결 및 세션 관리(XMLA)</span><span class="sxs-lookup"><span data-stu-id="b7b24-102">Managing Connections and Sessions (XMLA)</span></span>
  <span data-ttu-id="b7b24-103">*상태 저장* 는 서버에서 메서드 호출 사이에 클라이언트의 id와 컨텍스트를 유지 하는 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-103">*Statefulness* is a condition during which the server preserves the identity and context of a client between method calls.</span></span> <span data-ttu-id="b7b24-104">*상태 비저장* 는 서버에서 메서드 호출이 완료 된 후 클라이언트의 id와 컨텍스트를 기억할 수 없는 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-104">*Statelessness* is a condition during which the server does not remember the identity and context of a client after a method call finishes.</span></span>  
  
 <span data-ttu-id="b7b24-105">상태 저장를 제공 하기 위해 XML for Analysis (XMLA)는 일련의 문을 함께 수행 하는 데 사용할 수 있는 *세션* 을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-105">To provide statefulness, XML for Analysis (XMLA) supports *sessions* that allow a series of statements to be performed together.</span></span> <span data-ttu-id="b7b24-106">예를 들어, 이러한 일련의 문을 사용하여 후속 쿼리에서 사용할 계산 멤버를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-106">An example of such a series of statements would be the creation of a calculated member that is to be used in subsequent queries.</span></span>  
  
 <span data-ttu-id="b7b24-107">일반적으로 XMLA의 세션은 OLE DB 2.6 사양에 설명된 다음과 같은 동작을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-107">In general, sessions in XMLA follow the following behavior outlined by the OLE DB 2.6 specification:</span></span>  
  
-   <span data-ttu-id="b7b24-108">세션에는 트랜잭션 및 명령 컨텍스트 범위가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-108">Sessions define transaction and command context scope.</span></span>  
  
-   <span data-ttu-id="b7b24-109">단일 세션 컨텍스트에서 여러 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-109">Multiple commands can be run in the context of a single session.</span></span>  
  
-   <span data-ttu-id="b7b24-110">XMLA 컨텍스트의 트랜잭션은 [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) 메서드와 함께 전송 되는 공급자별 명령을 통해 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-110">Support for transactions in the XMLA context is through provider-specific commands sent with the [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method.</span></span>  
  
 <span data-ttu-id="b7b24-111">XMLA에는 느슨하게 연결된 환경에서 잠금을 구현하기 위해 DAV(Distributed Authoring and Versioning) 프로토콜에서 사용하는 방법과 비슷한 모드로 웹 환경에서 세션을 지원하는 방법이 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-111">XMLA defines a way to support sessions in a Web environment in a mode similar to the approach used by the Distributed Authoring and Versioning (DAV) protocol to implement locking in a loosely coupled environment.</span></span> <span data-ttu-id="b7b24-112">이 구현은 공급자가 제한 시간, 연결 오류 등의 여러 가지 이유로 세션을 만료시킬 수 있다는 점에서 DAV와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-112">This implementation parallels DAV in that the provider is allowed to expire sessions for various reasons (for example, a timeout or connection error).</span></span> <span data-ttu-id="b7b24-113">세션이 지원되는 경우 웹 서비스는 다시 시작해야 하는 중단된 명령 집합을 인식하고 처리할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-113">When sessions are supported, Web services must be aware and ready to handle interrupted sets of commands that must be restarted.</span></span>  
  
 <span data-ttu-id="b7b24-114">W3C(World Wide Web Consortium) SOAP(Simple Object Access Protocol) 사양에서는 SOAP 헤더를 사용하여 SOAP 메시지 위에 새 프로토콜을 작성할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-114">The World Wide Web Consortium (W3C) Simple Object Access Protocol (SOAP) specification recommends using SOAP headers for building up new protocols on top of SOAP messages.</span></span> <span data-ttu-id="b7b24-115">다음 표에서는 세션 시작, 유지 관리 및 닫기를 위해 XMLA에 정의된 SOAP 헤더 요소 및 특성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-115">The following table lists the SOAP header elements and attributes that XMLA defines for initiating, maintaining, and closing a session.</span></span>  
  
|<span data-ttu-id="b7b24-116">SOAP 헤더</span><span class="sxs-lookup"><span data-stu-id="b7b24-116">SOAP header</span></span>|<span data-ttu-id="b7b24-117">Description</span><span class="sxs-lookup"><span data-stu-id="b7b24-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b7b24-118">BeginSession</span><span class="sxs-lookup"><span data-stu-id="b7b24-118">BeginSession</span></span>|<span data-ttu-id="b7b24-119">이 헤더는 공급자에게 새 세션을 만들도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-119">This header requests the provider to create a new session.</span></span> <span data-ttu-id="b7b24-120">공급자는 새 세션을 생성한 후 SOAP 응답에 있는 세션 헤더의 일부로 세션 ID를 반환하여 응답해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-120">The provider should respond by constructing a new session and returning the session ID as part of the Session header in the SOAP response.</span></span>|  
|<span data-ttu-id="b7b24-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="b7b24-121">SessionId</span></span>|<span data-ttu-id="b7b24-122">값 영역에는 세션의 나머지 부분에서 각 메서드 호출에 사용해야 하는 세션 ID가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-122">The value area contains the session ID that must be used in each method call for the rest of the session.</span></span> <span data-ttu-id="b7b24-123">SOAP 응답에 있는 공급자가 이 태그를 보내며 클라이언트도 이 특성을 각 세션 헤더 요소와 함께 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-123">The provider in the SOAP response sends this tag and the client must also send this attribute with each Session header element.</span></span>|  
|<span data-ttu-id="b7b24-124">세션</span><span class="sxs-lookup"><span data-stu-id="b7b24-124">Session</span></span>|<span data-ttu-id="b7b24-125">세션에서 발생한 모든 메서드 호출에서 이 헤더를 사용해야 하며 세션 ID가 헤더의 값 영역에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-125">For every method call that occurs in the session, this header must be used, and the session ID must be included in the value area of the header.</span></span>|  
|<span data-ttu-id="b7b24-126">EndSession</span><span class="sxs-lookup"><span data-stu-id="b7b24-126">EndSession</span></span>|<span data-ttu-id="b7b24-127">세션을 종료하려면 이 헤더를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-127">To terminate the session, use this header.</span></span> <span data-ttu-id="b7b24-128">세션 ID가 값 영역과 함께 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-128">The session ID must be included with the value area.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="b7b24-129">세션 ID는 세션이 유효한 상태를 유지함을 보장하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-129">A session ID does not guarantee that a session stays valid.</span></span> <span data-ttu-id="b7b24-130">세션이 만료된 경우(예를 들어, 세션의 시간이 초과되거나 연결이 끊어진 경우) 공급자는 해당 세션의 동작을 종료하고 롤백할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-130">If the session expires (for example, if it times out or the connection is lost), the provider can choose to end and roll back that session's actions.</span></span> <span data-ttu-id="b7b24-131">결과적으로 세션 ID에 대한 클라이언트의 모든 후속 메서드 호출은 세션이 유효하지 않음을 나타내는 오류가 발생하면서 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-131">As a result, all subsequent method calls from the client on a session ID fail with an error signaling a session that is not valid.</span></span> <span data-ttu-id="b7b24-132">클라이언트는 이 조건을 처리해야 하며 세션 메서드 호출을 처음부터 다시 보낼 준비를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-132">A client should handle this condition and be prepared to resend the session method calls from the beginning.</span></span>  
  
## <a name="legacy-code-example"></a><span data-ttu-id="b7b24-133">레거시 예제 코드</span><span class="sxs-lookup"><span data-stu-id="b7b24-133">Legacy Code Example</span></span>  
 <span data-ttu-id="b7b24-134">다음 예제에서는 세션이 지원되는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-134">The following example shows how sessions are supported.</span></span>  
  
1.  <span data-ttu-id="b7b24-135">세션을 시작하기 위해 SOAP의 BeginSession 헤더를 클라이언트의 아웃바운드 XMLA 메서드 호출에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-135">To begin the session, add a BeginSession header in SOAP to the outbound XMLA method call from the client.</span></span> <span data-ttu-id="b7b24-136">처음에는 세션 ID를 알지 못하므로 값 영역이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-136">The value area is initially blank because the session ID is not yet known.</span></span>  
  
    ```  
    <SOAP-ENV:Envelope  
       xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
       SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
       <SOAP-ENV:Header>  
          <XA:BeginSession  
             xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
             xsi:type="xsd:int"  
             mustUnderstand="1"/>  
       </SOAP-ENV:Header>  
       <SOAP-ENV:Body>  
          ...<!-- Discover or Execute call goes here.-->  
       </SOAP-ENV:Body>  
    </SOAP-ENV:Envelope>  
    ```  
  
2.  <span data-ttu-id="b7b24-137">공급자의 SOAP 응답 메시지는 XMLA 헤더 태그를 사용 하 여 반환 헤더 영역에 세션 ID를 포함 합니다 \<SessionId> .</span><span class="sxs-lookup"><span data-stu-id="b7b24-137">The SOAP response message from the provider includes the session ID in the return header area, using the XMLA header tag \<SessionId>.</span></span>  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
3.  <span data-ttu-id="b7b24-138">세션의 각 메서드 호출에는 공급자가 반환한 세션 ID가 포함된 세션 헤더가 추가되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-138">For each method call in the session, the Session header must be added, containing the session ID returned from the provider.</span></span>  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
4.  <span data-ttu-id="b7b24-139">세션이 완료 되 면 \<EndSession> 관련 된 세션 ID 값을 포함 하는 태그가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7b24-139">When the session is complete, the \<EndSession> tag is used, containing the related session ID value.</span></span>  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:EndSession  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          xsi:type="xsd:int"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b7b24-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b7b24-140">See Also</span></span>  
 [<span data-ttu-id="b7b24-141">Analysis Services에서 XMLA를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="b7b24-141">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
