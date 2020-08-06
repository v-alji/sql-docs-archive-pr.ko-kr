---
title: 웹 서버 정보 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7b461ed26b3e234f083add3312e256e164efc9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649468"
---
# <a name="web-server-information"></a><span data-ttu-id="20056-102">웹 서버 정보</span><span class="sxs-lookup"><span data-stu-id="20056-102">Web Server Information</span></span>
  <span data-ttu-id="20056-103">병합 복제에 대해 웹 동기화 옵션을 사용하려면 웹 서버 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="20056-103">Web server information is required to use the Web synchronization option for merge replication.</span></span> <span data-ttu-id="20056-104">웹 동기화를 구성하는 방법은 [웹 동기화 구성](configure-web-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20056-104">For information about configuring Web synchronization, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="20056-105">옵션</span><span class="sxs-lookup"><span data-stu-id="20056-105">Options</span></span>  
 <span data-ttu-id="20056-106">**웹 서버 주소**</span><span class="sxs-lookup"><span data-stu-id="20056-106">**Web server address**</span></span>  
 <span data-ttu-id="20056-107">**게시 속성** 대화 상자의 **FTP 스냅샷 및 인터넷** 페이지에서 웹 서버 주소를 지정한 경우 이 주소가 입력란에 기본값으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20056-107">If you specified a Web server address in the **FTP Snapshot andInternet** page of the **Publication Properties** dialog box, it appears in this text box as a default.</span></span> <span data-ttu-id="20056-108">해당 기본값을 사용하거나 이 구독을 동기화하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 인터넷 정보 서비스(IIS) 서버에 대해 정규화된 웹 서버 주소를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="20056-108">Either accept the default or enter a fully qualified Web server address for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) server that synchronizes this subscription.</span></span>  
  
 <span data-ttu-id="20056-109">**각 구독자를 웹 서버에 연결하는 방법을 선택하십시오.**</span><span class="sxs-lookup"><span data-stu-id="20056-109">**How will each Subscriber connect to the Web server?**</span></span>  
 <span data-ttu-id="20056-110">웹 서버에 연결할 때 사용할 인증 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20056-110">Specify the type of authentication used to connect to the Web server.</span></span> <span data-ttu-id="20056-111">IIS 서버에 연결할 때는 SSL(Secure Sockets Layer)과 함께 기본 인증을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="20056-111">It is recommended to use Basic Authentication for connections to the IIS server in conjunction with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="20056-112">기본 인증을 선택하는 경우 구독자에서 IIS 서버로 연결할 때 사용할 로그인 및 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="20056-112">If you select Basic Authentication, enter the login and password that will be used to connect from the Subscriber to the IIS server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20056-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20056-113">See Also</span></span>  
 <span data-ttu-id="20056-114">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="20056-114">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="20056-115">[끌어오기 구독 속성 보기 및 수정](view-and-modify-pull-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="20056-115">[View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md) </span></span>  
 <span data-ttu-id="20056-116">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="20056-116">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span></span>  
 <span data-ttu-id="20056-117">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="20056-117">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="20056-118">병합 복제에 대한 웹 동기화</span><span class="sxs-lookup"><span data-stu-id="20056-118">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
