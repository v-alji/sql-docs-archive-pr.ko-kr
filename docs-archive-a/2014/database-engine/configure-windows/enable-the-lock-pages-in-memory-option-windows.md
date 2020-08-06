---
title: 메모리에 페이지 잠금 옵션 설정(Windows) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Lock Pages in Memory option
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13290940c3a94a7ba79582d892a5e28670f24b29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651270"
---
# <a name="enable-the-lock-pages-in-memory-option-windows"></a><span data-ttu-id="5617c-102">Lock Pages in Memory 옵션 설정(Windows)</span><span class="sxs-lookup"><span data-stu-id="5617c-102">Enable the Lock Pages in Memory Option (Windows)</span></span>
  <span data-ttu-id="5617c-103">이 Windows 정책은 데이터를 실제 메모리에 유지하는 프로세스를 사용하여 시스템이 디스크의 가상 메모리로 데이터를 페이징하지 않도록 방지할 수 있는 계정을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-103">This Windows policy determines which accounts can use a process to keep data in physical memory, preventing the system from paging the data to virtual memory on disk.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5617c-104">메모리의 페이지를 잠그면 메모리를 디스크로 페이징할 때 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-104">Locking pages in memory may boost performance when paging memory to disk is expected.</span></span>  
  
 <span data-ttu-id="5617c-105">Windows 그룹 정책 도구(gpedit.msc)를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 사용되는 계정에 대해 이 정책을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-105">Use the Windows Group Policy tool (gpedit.msc) to enable this policy for the account used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5617c-106">이 정책을 변경하려면 시스템 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-106">You must be a system administrator to change this policy.</span></span>  
  
### <a name="to-enable-the-lock-pages-in-memory-option"></a><span data-ttu-id="5617c-107">메모리의 페이지 잠금 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="5617c-107">To enable the lock pages in memory option</span></span>  
  
1.  <span data-ttu-id="5617c-108">**시작** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-108">On the **Start** menu, click **Run**.</span></span> <span data-ttu-id="5617c-109">**열기** 상자에을 입력 `gpedit.msc` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-109">In the **Open** box, type `gpedit.msc`.</span></span>  
  
2.  <span data-ttu-id="5617c-110">**로컬 그룹 정책 편집기** 콘솔에서 **컴퓨터 구성**을 확장한 다음 **Windows 설정**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-110">On the **Local Group Policy Editor** console, expand **Computer Configuration**, and then expand **Windows Settings**.</span></span>  
  
3.  <span data-ttu-id="5617c-111">**보안 설정**을 확장한 다음 **로컬 정책**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-111">Expand **Security Settings**, and then expand **Local Policies**.</span></span>  
  
4.  <span data-ttu-id="5617c-112">**사용자 권한 할당** 폴더를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-112">Select the **User Rights Assignment** folder.</span></span>  
  
     <span data-ttu-id="5617c-113">세부 정보 창에 정책이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-113">The policies will be displayed in the details pane.</span></span>  
  
5.  <span data-ttu-id="5617c-114">세부 정보 창에서 **메모리의 페이지 잠그기**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-114">In the pane, double-click **Lock pages in memory**.</span></span>  
  
6.  <span data-ttu-id="5617c-115">**로컬 보안 설정 – 메모리의 페이지 잠그기** 대화 상자에서 **사용자 또는 그룹 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-115">In the **Local Security Setting - Lock pages in memory** dialog box, click **Add User or Group**.</span></span>  
  
7.  <span data-ttu-id="5617c-116">**사용자, 서비스 계정 또는 그룹 선택** 대화 상자에서 sqlservr.exe를 실행할 권한이 있는 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-116">In the **Select Users, Service Accounts, or Groups** dialog box, add an account with privileges to run sqlservr.exe.</span></span>  
  
8.  <span data-ttu-id="5617c-117">이 변경 사항을 적용하려면 로그아웃한 다음 다시 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="5617c-117">Log out and then log back in for this change to take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5617c-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5617c-118">See Also</span></span>  
 [<span data-ttu-id="5617c-119">서버 메모리 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="5617c-119">Server Memory Server Configuration Options</span></span>](server-memory-server-configuration-options.md)  
  
  
