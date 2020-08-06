---
title: MSSQLSERVER_17832 | Microsoft 문서
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17828 (Database Engine error)
- maxtokensize
- 17832 (Database Engine error)
- login packet (bad)
ms.assetid: bd56ffe4-0855-4ada-8aca-251fbc6ff2ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dba214e2cce04ff2583e12ae7cee9b54373390a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729543"
---
# <a name="mssqlserver_17832"></a><span data-ttu-id="96148-102">MSSQLSERVER_17832</span><span class="sxs-lookup"><span data-stu-id="96148-102">MSSQLSERVER_17832</span></span>
    
## <a name="details"></a><span data-ttu-id="96148-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="96148-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="96148-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="96148-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="96148-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="96148-105">Event ID</span></span>|<span data-ttu-id="96148-106">17832</span><span class="sxs-lookup"><span data-stu-id="96148-106">17832</span></span>|  
|<span data-ttu-id="96148-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="96148-107">Event Source</span></span>|<span data-ttu-id="96148-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="96148-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="96148-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="96148-109">Component</span></span>|<span data-ttu-id="96148-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="96148-110">SQLEngine</span></span>|  
|<span data-ttu-id="96148-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="96148-111">Symbolic Name</span></span>|<span data-ttu-id="96148-112">SRV_BAD_LOGIN_PKT</span><span class="sxs-lookup"><span data-stu-id="96148-112">SRV_BAD_LOGIN_PKT</span></span>|  
|<span data-ttu-id="96148-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="96148-113">Message Text</span></span>|<span data-ttu-id="96148-114">연결을 여는 데 사용한 로그인 패킷이 구조적으로 잘못되었습니다. 연결이 닫혔습니다.</span><span class="sxs-lookup"><span data-stu-id="96148-114">The login packet used to open the connection is structurally invalid; the connection has been closed.</span></span> <span data-ttu-id="96148-115">클라이언트 라이브러리 공급업체에 문의하십시오.%.\*ls</span><span class="sxs-lookup"><span data-stu-id="96148-115">Please contact the vendor of the client library.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="96148-116">설명</span><span class="sxs-lookup"><span data-stu-id="96148-116">Explanation</span></span>  
 <span data-ttu-id="96148-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 컴퓨터에서 클라이언트 로그인 패킷을 처리하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="96148-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer was unable to process the client login packet.</span></span> <span data-ttu-id="96148-118">이 문제는 패킷이 잘못 만들어졌거나 전송 중에 손상되었기 때문에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96148-118">This may be because the packet was created improperly or because the packet was damaged during transmission.</span></span> <span data-ttu-id="96148-119">또한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 컴퓨터의 구성 때문에 이 문제가 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96148-119">It can also be caused by the configuration of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="96148-120">나열된 IP 주소는 클라이언트 컴퓨터의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="96148-120">The IP address listed is the address of the client computer.</span></span>  
  
### <a name="more-information"></a><span data-ttu-id="96148-121">추가 정보</span><span class="sxs-lookup"><span data-stu-id="96148-121">More Information</span></span>  
 <span data-ttu-id="96148-122">Kerberos 환경에서 Windows 인증을 사용할 경우 클라이언트는 PAC(Privilege Attribute Certificate)가 포함된 Kerberos 티켓을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="96148-122">When using Windows Authentication in a Kerberos environment, a client receives a Kerberos ticket that contains a Privilege Attribute Certificate (PAC).</span></span> <span data-ttu-id="96148-123">PAC에는 사용자가 속한 그룹, 사용자가 가지고 있는 권한, 사용자에게 적용되는 정책 등 다양한 유형의 인증 데이터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96148-123">The PAC contains various types of authorization data including groups that the user is a member of, rights the user has, and what policies apply to the user.</span></span> <span data-ttu-id="96148-124">클라이언트가 Kerberos 티켓을 수신하면 PAC에 포함된 정보가 사용자의 액세스 토큰을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="96148-124">When the client receives the Kerberos ticket, the information contained in the PAC is used to generate the user's access token.</span></span> <span data-ttu-id="96148-125">클라이언트는 이 토큰을 로그인 패킷의 일부로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 컴퓨터에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="96148-125">The client presents the token to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer as part of the login packet.</span></span>  
  
 <span data-ttu-id="96148-126">패킷이 잘못 만들어졌거나 전송 중에 손상된 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 문제에 대한 추가 정보를 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="96148-126">If the token was improperly created or damaged during transmission, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot offer additional information about the problem.</span></span>  
  
 <span data-ttu-id="96148-127">사용자가 여러 그룹의 멤버이거나 많은 정책을 사용하는 경우 이러한 것들을 모두 나열하기 위해 토큰이 정상보다 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96148-127">When the user is a member of many groups or has many policies, the token may grow larger than normal to list them all.</span></span> <span data-ttu-id="96148-128">토큰이 서버 컴퓨터의 **MaxTokenSize** 값보다 커질 경우 클라이언트가 GNE(일반 네트워크 오류)에 연결하지 못하고 오류 17832가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96148-128">If the token grows larger than the **MaxTokenSize** value of the server computer, the client fails to connect with a General Network Error (GNE) and error 17832 can occur.</span></span> <span data-ttu-id="96148-129">이 문제는 그룹이나 정책이 많은 일부 사용자에게만 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96148-129">This problem may affect only some users: users with many groups or policies.</span></span> <span data-ttu-id="96148-130">서버 컴퓨터의 **MaxTokenSize** 값에 문제가 있을 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그의 오류 17832와 함께 상태가 9인 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="96148-130">When the problem is the **MaxTokenSize** value of the server computer, error 17832 in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log will be accompanied by an error with state 9.</span></span> <span data-ttu-id="96148-131">Kerberos 및 **MaxTokenSize**에 대한 자세한 내용은 [KB327825](https://support.microsoft.com/kb/327825)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="96148-131">For additional details about the Kerberos and **MaxTokenSize**, see [KB327825](https://support.microsoft.com/kb/327825).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="96148-132">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="96148-132">User Action</span></span>  
 <span data-ttu-id="96148-133">이 문제를 해결하려면 서버 컴퓨터의 **MaxTokenSize** 값을 조직에 있는 모든 사용자의 토큰 중 가장 큰 토큰을 포함할 수 있는 충분한 크기로 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="96148-133">To resolve this problem, increase the **MaxTokenSize** value of the server computer, to a size large enough to contain the largest token of any user in your organization.</span></span> <span data-ttu-id="96148-134">조직에 맞는 올바른 토큰 크기를 조사하려면 **Tokensz** 애플리케이션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="96148-134">To research the correct token size for your organization, consider using the **Tokensz** application.</span></span>   
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="96148-135">**서버 컴퓨터에서 MaxTokenSize를 변경 하려면**</span><span class="sxs-lookup"><span data-stu-id="96148-135">**To change the MaxTokenSize  on the server computer**</span></span>  
  
1.  <span data-ttu-id="96148-136">**시작** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96148-136">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="96148-137">을 입력 한 `regedit` 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="96148-137">Type `regedit`, and then click **OK**.</span></span> <span data-ttu-id="96148-138">**사용자 계정 컨트롤** 대화 상자가 열리면 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96148-138">(If the **User Account Control** dialog box appears, click **Continue**.)</span></span>  
  
3.  <span data-ttu-id="96148-139">**HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Lsa\Kerberos\Parameters**로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="96148-139">Navigate to **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Lsa\Kerberos\Parameters**.</span></span>  
  
4.  <span data-ttu-id="96148-140">**MaxTokenSize** 매개 변수가 없으면 **Parameters**를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 다음 **DWORD(32비트) 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96148-140">If the **MaxTokenSize** parameter is not present, right-click **Parameters**, point to **New**, and then click **DWORD (32-bit)** Value.</span></span> <span data-ttu-id="96148-141">이 레지스트리 항목의 이름을 **MaxTokenSize**로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="96148-141">Name the registry entry **MaxTokenSize**.</span></span>  
  
5.  <span data-ttu-id="96148-142">**MaxTokenSize**를 마우스 오른쪽 단추를 클릭한 다음 **수정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96148-142">Right-click **MaxTokenSize**, and then click **Modify**.</span></span>  
  
6.  <span data-ttu-id="96148-143">**값 데이터** 상자에 원하는 **MaxTokenSize** 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="96148-143">In the **Value data** box type the desired **MaxTokenSize** value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="96148-144">권장되는 최대 토큰 크기는 16진수 값 ffff(10진수 값 65535)입니다.</span><span class="sxs-lookup"><span data-stu-id="96148-144">Hexadecimal value ffff (decimal value 65535) is the maximum recommended token size.</span></span> <span data-ttu-id="96148-145">이 값을 제공하면 문제가 해결될 수도 있지만 컴퓨터 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96148-145">Providing this value would probably solve the problem, but could have negative computer-wide effects with regard to performance.</span></span> <span data-ttu-id="96148-146">조직에 있는 모든 사용자의 토큰 중 가장 큰 토큰을 허용하는 최소 **MaxTokenSize** 값을 설정하고 이 값을 입력하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="96148-146">We recommend that you establish the minimum **MaxTokenSize** value that allows for the largest token of any user in your organization and enter that value.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="96148-147">**레지스트리 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="96148-147">Close **Registry Editor**.</span></span>  
  
9. <span data-ttu-id="96148-148">컴퓨터를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="96148-148">Restart the computer.</span></span>  
  
  
