---
title: 정책 가져오기 대화 상자 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2601c21ea08d00bf77e9b97a5186f2d6d1200a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646978"
---
# <a name="import-policies-dialog-box"></a><span data-ttu-id="59880-102">정책 가져오기 대화 상자</span><span class="sxs-lookup"><span data-stu-id="59880-102">Import Policies Dialog Box</span></span>
  <span data-ttu-id="59880-103">이 대화 상자를 사용하여 XML 파일로 저장된 하나 이상의 정책과 해당 참조 조건을 현재 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59880-103">Use this dialog box to import one or more policies (and their referenced condition) that are saved as XML files, into the current [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="59880-104">옵션</span><span class="sxs-lookup"><span data-stu-id="59880-104">Options</span></span>  
 <span data-ttu-id="59880-105">**가져올 파일**</span><span class="sxs-lookup"><span data-stu-id="59880-105">**Files to import**</span></span>  
 <span data-ttu-id="59880-106">XML 파일에서 정책을 가져오려면 파일의 경로와 이름을 입력하거나 찾아보기 단추( **...** )를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="59880-106">To import a policy from an XML file, type the path and name of the file or use the Browse (**...**) button.</span></span>  
  
 <span data-ttu-id="59880-107">**가져온 항목으로 중복 항목 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="59880-107">**Replace duplicates with items imported**</span></span>  
 <span data-ttu-id="59880-108">이 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 이름이 같은 정책 또는 조건이 이미 있는 경우 기존 정책 또는 조건을 덮어쓰려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="59880-108">Select to overwrite any existing policy or condition of the same name if it already exists on this [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance.</span></span> <span data-ttu-id="59880-109">종속 정책이 있는 조건은 종속 정책도 덮어쓰지 않는 한 덮어쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59880-109">A condition with a dependent policy cannot be overwritten unless the dependent policy is also being overwritten.</span></span> <span data-ttu-id="59880-110">이 옵션을 선택하지 않으면 같은 조건 식을 사용하는 기존 조건으로 인해 오류가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="59880-110">If this option is not selected, an existing condition that is using the same condition expression will not cause an error.</span></span>  
  
 <span data-ttu-id="59880-111">**정책 상태**</span><span class="sxs-lookup"><span data-stu-id="59880-111">**Policy state**</span></span>  
 <span data-ttu-id="59880-112">가져온 정책에서 원하는 상태를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="59880-112">Select the state that you want for the imported policy:</span></span>  
  
-   <span data-ttu-id="59880-113">**가져올 때 정책 상태 유지**</span><span class="sxs-lookup"><span data-stu-id="59880-113">**Preserve policy state on import**</span></span>  
  
-   <span data-ttu-id="59880-114">**가져올 때 모든 정책을 사용할 수 있도록 설정**</span><span class="sxs-lookup"><span data-stu-id="59880-114">**Enable all policies on import**</span></span>  
  
-   <span data-ttu-id="59880-115">**가져올 때 모든 정책을 사용할 수 없도록 설정**</span><span class="sxs-lookup"><span data-stu-id="59880-115">**Disable all policies on import**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59880-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59880-116">See Also</span></span>  
 <span data-ttu-id="59880-117">[정책 기반 관리를 사용하여 서버 관리](administer-servers-by-using-policy-based-management.md) </span><span class="sxs-lookup"><span data-stu-id="59880-117">[Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md) </span></span>  
 <span data-ttu-id="59880-118">[정책 기반 관리 정책 가져오기](import-a-policy-based-management-policy.md) </span><span class="sxs-lookup"><span data-stu-id="59880-118">[Import a Policy-Based Management Policy](import-a-policy-based-management-policy.md) </span></span>  
 [<span data-ttu-id="59880-119">정책 기반 관리 정책 내보내기</span><span class="sxs-lookup"><span data-stu-id="59880-119">Export a Policy-Based Management Policy</span></span>](export-a-policy-based-management-policy.md)  
  
  
