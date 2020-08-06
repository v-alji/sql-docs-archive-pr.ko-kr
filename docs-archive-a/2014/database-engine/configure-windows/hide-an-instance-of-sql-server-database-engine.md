---
title: SQL Server 데이터베이스 엔진의 인스턴스 숨기기 | Microsoft Docs
ms.custom: ''
ms.date: 08/19/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], hiding instances
- hiding instances of Database Engine
ms.assetid: 392de21a-57fa-4a69-8237-ced8ca86ed1d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d2b3287c5d4d747ccb3511461341d5aed8ff765d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729827"
---
# <a name="hide-an-instance-of-sql-server-database-engine"></a><span data-ttu-id="d2659-102">SQL Server 데이터베이스 엔진의 인스턴스 숨기기</span><span class="sxs-lookup"><span data-stu-id="d2659-102">Hide an Instance of SQL Server Database Engine</span></span>
  <span data-ttu-id="d2659-103">이 항목에서는 SQL Server 구성 관리자를 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 인스턴스를 숨기는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-103">This topic describes how to hide an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d2659-104">는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스를 사용하여 컴퓨터에 설치된 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-104">uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service to enumerate instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] installed on the computer.</span></span> <span data-ttu-id="d2659-105">이렇게 하면 클라이언트 애플리케이션에서 서버를 검색하고 클라이언트가 같은 컴퓨터에 있는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 여러 인스턴스를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-105">This enables client applications to browse for a server, and helps clients distinguish between multiple instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the same computer.</span></span> <span data-ttu-id="d2659-106">다음 절차를 통해 SQL Server Browser 서비스에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 찾아보기 **단추를 사용하여 인스턴스를 찾으려고 하는 클라이언트 컴퓨터에** 인스턴스를 노출하지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-106">You can use the following procedure to prevent the SQL Server Browser service from exposing an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to client computers that try to locate the instance by using the **Browse** button.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d2659-107">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="d2659-107">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-hide-an-instance-of-the-sql-server-database-engine"></a><span data-ttu-id="d2659-108">SQL Server 데이터베이스 엔진의 인스턴스를 숨기려면</span><span class="sxs-lookup"><span data-stu-id="d2659-108">To hide an instance of the SQL Server Database Engine</span></span>  
  
1.  <span data-ttu-id="d2659-109">**SQL Server 구성 관리자**에서 **SQL Server 네트워크 구성**을 확장하고 *\<server instance>* 에 대한 **프로토콜**을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-109">In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, right-click **Protocols for** *\<server instance>*, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="d2659-110">**플래그** 탭의 **인스턴스 숨기기** 상자에서 **예**를 선택한 다음 **확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-110">On the **Flags** tab, in the **HideInstance** box, select **Yes**, and then click **OK** to close the dialog box.</span></span> <span data-ttu-id="d2659-111">변경 내용이 새 연결에 대해 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-111">The change takes effect immediately for new connections.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2659-112">설명</span><span class="sxs-lookup"><span data-stu-id="d2659-112">Remarks</span></span>  
 <span data-ttu-id="d2659-113">명명된 인스턴스를 숨기면 브라우저 서비스가 실행되고 있더라도 숨겨진 인스턴스에 연결할 때 연결 문자열에 포트 번호를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-113">If you hide a named instance, you will need to provide the port number in the connection string to connect to the hidden instance, even if the browser service is running.</span></span> <span data-ttu-id="d2659-114">명명된 숨겨진 인스턴스에 대한 동적 포트 대신 정적 포트를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-114">We recommend that you use a static port instead of a dynamic port for the named hidden instance.</span></span>  
  <span data-ttu-id="d2659-115">자세한 내용은 [특정 TCP 포트로 수신하도록 서버 구성&#40;SQL Server 구성 관리자&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2659-115">For more information, see [Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md).</span></span>  
  
### <a name="clustering"></a><span data-ttu-id="d2659-116">Clustering</span><span class="sxs-lookup"><span data-stu-id="d2659-116">Clustering</span></span>  
 <span data-ttu-id="d2659-117">클러스터된 명명된 인스턴스를 숨기면 클러스터 서비스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-117">If you hide a clustered named instance, cluster service may not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d2659-118">이렇게 되면 클러스터 인스턴스의 **IsAlive** 검사가 실패하게 되고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]은(는) 오프라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-118">This will cause the cluster instance's **IsAlive** check to fail and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will go offline.</span></span> <span data-ttu-id="d2659-119">인스턴스에 대해 구성한 정적 포트를 반영하도록 클러스터된 인스턴스의 모든 노드에서 별칭을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-119">We recommend that you create an alias in all the nodes of the clustered instance to reflect the static port that you configured for the instance.</span></span>  
 <span data-ttu-id="d2659-120">자세한 내용은 [클라이언트에서 사용할 서버 별칭 만들기 또는 삭제&#40;SQL Server 구성 관리자&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2659-120">For more information, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md).</span></span>  
  
 <span data-ttu-id="d2659-121">클러스터된 명명된 인스턴스를 숨기면 **LastConnect** 레지스트리 키(**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI11.0\LastConnect**)에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 수신 중인 포트가 아닌 다른 포트가 있는 경우 클러스터 서비스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-121">If you hide a clustered named instance, cluster service may not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if the **LastConnect** registry key (**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI11.0\LastConnect**) has a different port than the port that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening on.</span></span> <span data-ttu-id="d2659-122">클러스터 서비스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할 수 없는 경우 다음과 유사한 오류가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2659-122">If the cluster service is unable to make a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you might see an error similar to the following:</span></span>  
<span data-ttu-id="d2659-123">**이벤트 ID: 1001: 이벤트 이름: 장애 조치(failover) 클러스터링 리소스 교착상태.**</span><span class="sxs-lookup"><span data-stu-id="d2659-123">**Event ID: 1001: Event Name: Failover clustering resource deadlock.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2659-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2659-124">See Also</span></span>  
 <span data-ttu-id="d2659-125">[서버 네트워크 구성](server-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d2659-125">[Server Network Configuration](server-network-configuration.md) </span></span>  
 <span data-ttu-id="d2659-126">[SQL 가상 서버 클라이언트 연결에 대한 설명(영문)](https://support.microsoft.com/kb/273673) </span><span class="sxs-lookup"><span data-stu-id="d2659-126">[Description of SQL Virtual Server client connections](https://support.microsoft.com/kb/273673) </span></span>  
 [<span data-ttu-id="d2659-127">SQL Server라고 명명된 인스턴스에 정적 포트를 할당하고 일반적인 문제를 방지하는 방법(영문)</span><span class="sxs-lookup"><span data-stu-id="d2659-127">How to assign a static port to a SQL Server named instance - and avoid a common pitfall</span></span>](https://blogs.msdn.com/b/arvindsh/archive/2012/09/08/how-to-assign-a-static-port-to-a-sql-server-named-instance-and-avoid-a-common-pitfall.aspx)  
  
  
