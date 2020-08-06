---
title: 큐 판독기 에이전트 보안 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.QRA.f1
helpviewer_keywords:
- Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 22a5e5751184b626ab1af86f01782a42028b5ced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659940"
---
# <a name="queue-reader-agent-security"></a><span data-ttu-id="e5c96-102">큐 판독기 에이전트 보안</span><span class="sxs-lookup"><span data-stu-id="e5c96-102">Queue Reader Agent Security</span></span>
  <span data-ttu-id="e5c96-103">**큐 판독기 에이전트 보안** 대화 상자를 사용하여 큐 판독기 에이전트가 실행 중이며 배포자에 로컬 연결을 설정하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5c96-103">The **Queue Reader Agent Security** dialog box allows you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Queue Reader Agent runs and makes local connections to the Distributor.</span></span> <span data-ttu-id="e5c96-104">에이전트는 **게시자 속성** 대화 상자( **배포자 속성** 대화 상자에서 사용 가능)에서 지정한 계정을 사용하여 게시자에 연결하고, 구독에 대한 배포 에이전트와 동일한 컨텍스트를 사용하여 구독자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c96-104">The agent connects to the Publisher using the account specified in the **Publisher Properties** dialog box (available from the **Distributor Properties** dialog box); the agent connects to the Subscriber using the same context as the Distribution Agent for the subscription.</span></span> <span data-ttu-id="e5c96-105">자세한 내용은 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5c96-105">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="e5c96-106">계정은 올바른 암호가 지정된 유효한 것이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c96-106">The account must be valid with the correct password specified.</span></span> <span data-ttu-id="e5c96-107">계정 및 암호의 유효성은 에이전트를 실행할 때 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c96-107">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e5c96-108">옵션</span><span class="sxs-lookup"><span data-stu-id="e5c96-108">Options</span></span>  
 <span data-ttu-id="e5c96-109">**프로세스 계정**</span><span class="sxs-lookup"><span data-stu-id="e5c96-109">**Process account**</span></span>  
 <span data-ttu-id="e5c96-110">배포자에서 큐 판독기 에이전트가 실행되는 Windows 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c96-110">Enter a Windows account under which the Queue Reader Agent runs at the Distributor.</span></span> <span data-ttu-id="e5c96-111">지정한 Windows 계정은 적어도 배포 데이터베이스에 포함된 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c96-111">The Windows account you specify must at minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
 <span data-ttu-id="e5c96-112">**암호** 및 **암호 확인**</span><span class="sxs-lookup"><span data-stu-id="e5c96-112">**Password** and **Confirm password**</span></span>  
 <span data-ttu-id="e5c96-113">Windows 계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c96-113">Enter the password for the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c96-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5c96-114">See Also</span></span>  
 <span data-ttu-id="e5c96-115">[복제의 로그인 및 암호 관리](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="e5c96-115">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="e5c96-116">[복제 에이전트 보안 모델](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="e5c96-116">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="e5c96-117">[복제 에이전트 개요](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="e5c96-117">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="e5c96-118">복제 보안을 위한 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="e5c96-118">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
