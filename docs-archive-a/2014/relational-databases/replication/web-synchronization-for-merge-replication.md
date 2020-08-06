---
title: 병합 복제에 대한 웹 동기화 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication synchronization [SQL Server replication]
- Internet [SQL Server replication], synchronization
- synchronization [SQL Server replication], Web Synchronization
- Web publishing [SQL Server replication], synchronization
- Web synchronization, about
- Web synchronization
ms.assetid: 84785aba-b2c1-4821-9e9d-a363c73dcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef7bf5a6f77d593a90508a0b69d02f8c0db04407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659938"
---
# <a name="web-synchronization-for-merge-replication"></a><span data-ttu-id="6377d-102">병합 복제에 대한 웹 동기화</span><span class="sxs-lookup"><span data-stu-id="6377d-102">Web Synchronization for Merge Replication</span></span>
  <span data-ttu-id="6377d-103">병합 복제에 대한 웹 동기화를 사용하면 HTTPS 프로토콜을 사용하여 데이터를 복제할 수 있으며 다음 시나리오에서도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-103">Web synchronization for merge replication lets you replicate data by using the HTTPS protocol, and is useful for the following scenarios:</span></span>

-   <span data-ttu-id="6377d-104">인터넷을 통해 모바일 사용자로부터 데이터 동기화</span><span class="sxs-lookup"><span data-stu-id="6377d-104">Synchronizing data from mobile users over the Internet.</span></span>

-   <span data-ttu-id="6377d-105">회사 방화벽을 통해 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 간 데이터 동기화</span><span class="sxs-lookup"><span data-stu-id="6377d-105">Synchronizing data between [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases across a corporate firewall.</span></span>

 <span data-ttu-id="6377d-106">예를 들어 출장 중인 영업 담당자가 웹 동기화를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-106">For example, a traveling sales representative can use Web synchronization.</span></span> <span data-ttu-id="6377d-107">[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]라는 회사의 영업 담당자는 전역에 있는 매장과 공급업체로 출장을 갑니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-107">The company, [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], has sales representatives that travel to various stores and suppliers throughout their regions.</span></span> <span data-ttu-id="6377d-108">장기 출장인 경우 담당자는 호텔에 머무르면서 매일 업무가 끝날 때마다 판매 데이터를 업로드하고 제품 업데이트를 다운로드할 수 있는 편리한 방법이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-108">On longer trips the representatives stay in hotels and need a convenient way to upload sales data and download any product updates at the end of each day.</span></span>

 <span data-ttu-id="6377d-109">[!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] IT 부서에서는 각 휴대용 컴퓨터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로 구성하고 웹 동기화를 사용할 수 있도록 병합 복제를 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-109">The [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] IT department has configured each portable computer with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and has enabled merge replication to use Web synchronization.</span></span> <span data-ttu-id="6377d-110">각 휴대용 컴퓨터의 병합 에이전트에는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 인터넷 정보 서비스(IIS)를 실행하는 컴퓨터에 설치된 복제 구성 요소를 가리키는 인터넷 URL이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-110">The Merge Agent on each portable computer has an Internet URL that points to the replication components that are installed on a computer that is running [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS).</span></span> <span data-ttu-id="6377d-111">이러한 구성 요소는 구독자와 게시자를 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-111">These components synchronize the Subscriber with the Publisher.</span></span> <span data-ttu-id="6377d-112">각 담당자는 이제 원격 전화 접속 연결을 사용하지 않고도 사용 가능한 임의의 인터넷 연결을 통해 연결을 설정하여 해당 데이터를 업로드 및 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-112">Each representative can now connect through any available Internet connection without using a remote dial-up connection, and can upload and download the appropriate data.</span></span> <span data-ttu-id="6377d-113">인터넷 연결은 SSL(Secure Sockets Layer)을 사용하므로 VPN(가상 프라이빗 네트워크)이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-113">The Internet connection uses Secure Sockets Layer (SSL); therefore, a virtual private network (VPN) is not required.</span></span>

 <span data-ttu-id="6377d-114">웹 동기화에 필요한 구성 요소를 구성하는 방법은 [웹 동기화 구성](configure-web-synchronization.md), [웹 동기화를 위한 IIS 구성](configure-iis-for-web-synchronization.md) 및 [웹 동기화를 위한 IIS 7 구성](configure-iis-7-for-web-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6377d-114">For information about how to configure the components that are required for Web synchronization, see [Configure Web Synchronization](configure-web-synchronization.md), [Configure IIS for Web Synchronization](configure-iis-for-web-synchronization.md), and [Configure IIS 7 for Web Synchronization](configure-iis-7-for-web-synchronization.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="6377d-115">웹 동기화는 데이터를 휴대용 컴퓨터, 핸드헬드 디바이스 및 기타 클라이언트와 동기화하기 위해 디자인되었으며</span><span class="sxs-lookup"><span data-stu-id="6377d-115">Web synchronization is designed for synchronizing data with portable computers, handheld devices, and other clients.</span></span> <span data-ttu-id="6377d-116">고용량 서버 간 애플리케이션을 위해 디자인되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-116">Web synchronization is not intended for high-volume server-to-server applications.</span></span>

## <a name="overview-of-how-web-synchronization-works"></a><span data-ttu-id="6377d-117">웹 동기화 작동 방식 개요</span><span class="sxs-lookup"><span data-stu-id="6377d-117">Overview of How Web Synchronization Works</span></span>
 <span data-ttu-id="6377d-118">웹 동기화를 사용하면 구독자의 업데이트가 패키지되어 IIS를 실행하는 컴퓨터에 HTTPS 프로토콜을 통해 XML 메시지로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-118">When Web synchronization is used, updates at the Subscriber are packaged and sent as an XML message to the computer that is running IIS by using the HTTPS protocol.</span></span> <span data-ttu-id="6377d-119">그러면 IIS를 실행하는 컴퓨터에서 명령을 이진 형식으로 게시자에 보냅니다. 이때 일반적으로 TCP/IP를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-119">The computer that is running IIS then sends the commands to the Publisher in a binary format, typically by using TCP/IP.</span></span> <span data-ttu-id="6377d-120">게시자의 업데이트 내용은 IIS를 실행하는 컴퓨터로 전송된 다음 구독자에 배달할 수 있도록 XML 메시지로 패키지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-120">Updates at the Publisher are sent to the computer that is running IIS and then packaged as an XML message for delivery to the Subscriber.</span></span>

 <span data-ttu-id="6377d-121">아래 그림에서는 병합 복제에 대한 웹 동기화에 관련된 구성 요소 중 일부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-121">The following illustration shows some of the components that are involved in Web synchronization for merge replication.</span></span>

 <span data-ttu-id="6377d-122">![웹 동기화 구성 요소 및 데이터 흐름](media/web-sync01.gif "웹 동기화 구성 요소 및 데이터 흐름")</span><span class="sxs-lookup"><span data-stu-id="6377d-122">![Web synchronization components and data flow](media/web-sync01.gif "Web synchronization components and data flow")</span></span>

 <span data-ttu-id="6377d-123">웹 동기화는 끌어오기 구독 전용 옵션이므로 병합 에이전트가 항상 구독자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-123">Web synchronization is an option only for pull subscriptions; therefore, a Merge Agent will always run on the Subscriber.</span></span> <span data-ttu-id="6377d-124">이 병합 에이전트는 표준 병합 에이전트, 병합 에이전트 ActiveX 컨트롤 또는 RMO(복제 관리 개체)를 통해 동기화를 제공하는 애플리케이션일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-124">This Merge Agent can be the standard Merge Agent, the Merge Agent ActiveX control, or an application that provides synchronization through Replication Management Objects (RMO).</span></span> <span data-ttu-id="6377d-125">IIS를 실행 하는 컴퓨터의 위치를 지정 하려면 병합 에이전트에 **-interneturl** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-125">To specify the location of the computer that is running IIS, use the **-InternetUrl** parameter for the Merge Agent.</span></span>

 <span data-ttu-id="6377d-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제 수신기(replisapi.dll)는 IIS를 실행하는 컴퓨터에 구성되어 있으며 게시자와 구독자에서 서버로 전송된 메시지를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-126">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener (Replisapi.dll) is configured on the computer that is running IIS and is responsible for handling messages that are sent to the server from the Publisher and Subscribers.</span></span> <span data-ttu-id="6377d-127">토폴로지에 있는 각 노드는 병합 복제 조정자(Replrec.dll)를 사용하여 XML 데이터 스트림을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-127">Each node in the topology handles the XML data stream by using the Merge Replication Reconciler (Replrec.dll).</span></span>

 <span data-ttu-id="6377d-128">웹 동기화에 참여하는 모든 컴퓨터에[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-128">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version is required for all computers that participate in Web synchronization.</span></span>

### <a name="synchronization-process"></a><span data-ttu-id="6377d-129">동기화 프로세스</span><span class="sxs-lookup"><span data-stu-id="6377d-129">Synchronization Process</span></span>
 <span data-ttu-id="6377d-130">다음은 동기화를 수행하는 동안 발생하는 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-130">The following steps occur during synchronization:</span></span>

1.  <span data-ttu-id="6377d-131">구독자에서 병합 에이전트가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-131">The Merge Agent is started at the Subscriber.</span></span> <span data-ttu-id="6377d-132">이 에이전트는 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-132">The agent does the following:</span></span>

    1.  <span data-ttu-id="6377d-133">구독 데이터베이스에 대해 SQL 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-133">Makes an SQL connection to the subscription database.</span></span>

    2.  <span data-ttu-id="6377d-134">데이터베이스에서 변경 내용을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-134">Extracts any changes from the database.</span></span>

    3.  <span data-ttu-id="6377d-135">IIS를 실행하는 컴퓨터에 HTTPS 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-135">Makes an HTTPS request to the computer that is running IIS.</span></span>

    4.  <span data-ttu-id="6377d-136">데이터 변경 내용을 XML 메시지로 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-136">Uploads data changes as an XML message.</span></span>

2.  <span data-ttu-id="6377d-137">IIS를 실행하는 컴퓨터에 호스팅되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제 수신기 및 병합 복제 조정자는 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-137">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener and Merge Replication Reconciler that are hosted on the computer that is running IIS do the following:</span></span>

    1.  <span data-ttu-id="6377d-138">HTTPS 요청에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-138">Respond to the HTTPS request.</span></span>

    2.  <span data-ttu-id="6377d-139">게시 데이터베이스에 대해 SQL 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-139">Make an SQL connection to the publication database.</span></span>

    3.  <span data-ttu-id="6377d-140">업로드한 변경 내용을 게시 데이터베이스에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-140">Apply the upload changes to the publication database.</span></span>

    4.  <span data-ttu-id="6377d-141">다운로드한 구독자 변경 내용을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-141">Extract the download changes for the Subscriber.</span></span>

    5.  <span data-ttu-id="6377d-142">병합 에이전트에 HTTPS 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-142">Send an HTTPS response back to the Merge Agent.</span></span>

3.  <span data-ttu-id="6377d-143">그러면 구독자의 병합 에이전트가 이 HTTPS 응답을 수락하고 다운로드한 변경 내용을 구독 데이터베이스에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="6377d-143">The Merge Agent at the Subscriber then accepts the HTTPS response and applies the download changes to the subscription database.</span></span>

## <a name="see-also"></a><span data-ttu-id="6377d-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6377d-144">See Also</span></span>
 <span data-ttu-id="6377d-145">웹 [동기화를 위한](topologies-for-web-synchronization.md) [웹 동기화 토폴로지 구성](configure-web-synchronization.md)</span><span class="sxs-lookup"><span data-stu-id="6377d-145">[Configure Web Synchronization](configure-web-synchronization.md) [Topologies for Web Synchronization](topologies-for-web-synchronization.md)</span></span>


