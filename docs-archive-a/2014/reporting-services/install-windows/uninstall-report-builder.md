---
title: 보고서 작성기 (보고서 작성기)의 독립 실행형 버전을 제거 합니다. Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 009538c6-4941-4393-b14b-9144cffdbdaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cda13248d1aa14ee3d57a951872d3ad8ded17da9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653739"
---
# <a name="uninstall-the-stand-alone-version-of-report-builder-report-builder"></a><span data-ttu-id="bf77a-102">독립 실행형 버전의 보고서 작성기 제거(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="bf77a-102">Uninstall the Stand-Alone Version of Report Builder (Report Builder)</span></span>
  <span data-ttu-id="bf77a-103">제어판 또는 명령줄에서 독립 실행형 버전의 보고서 작성기를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-103">You can uninstall the stand-alone version of Report Builder from the control panel or the command line.</span></span> <span data-ttu-id="bf77a-104">[!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] 버전 보고서 작성기는 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]를 제거해야만 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-104">You cannot uninstall the [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] version of Report Builder without uninstalling [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="bf77a-105">명령줄에서 보고서 작성기를 제거할 때 사용하는 구문은 보고서 작성기를 설치할 때 사용하는 구문과 동일하고 /i 옵션 대신 /x 옵션을 사용한다는 점만 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-105">Uninstalling Report Builder from the command line uses syntax that is identical to the syntax you use to install Report Builder, except you use the /x option instead of the /i option.</span></span> <span data-ttu-id="bf77a-106">제거할 때 사용하는 명령줄에는 /quiet 옵션과 기타 표준 옵션도 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-106">Command lines for uninstalling can also include the /quiet option and other standard options.</span></span> <span data-ttu-id="bf77a-107">보고서 작성기 Windows Installer 패키지(ReportBuilder3_x86.msi)가 이미 제거되었으면 명령줄을 사용하여 보고서 작성기를 제거하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-107">If the Report Builder Windows Installer Package (ReportBuilder3_x86.msi) has been removed, you cannot use the command line easily to uninstall Report Builder.</span></span> <span data-ttu-id="bf77a-108">해당 GUID를 사용하여 보고서 작성기를 제거하는 방법에 대한 자세한 내용은 MSDN 라이브러리에서 msiexec 프로그램에 대한 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf77a-108">To learn more about how you might be able to remove Report Builder by using its GUID, see the documentation for the msiexec program in the msdn library.</span></span>  
  
 <span data-ttu-id="bf77a-109">보고서 작성기용 폴더에 사용자 지정 파일이 포함되어 있으면 보고서 작성기를 제거할 때 해당 폴더와 파일이 유지되고</span><span class="sxs-lookup"><span data-stu-id="bf77a-109">If folders used by Report Builder include custom files, the folders and the files are preserved when Report Builder is removed.</span></span> <span data-ttu-id="bf77a-110">보고서 작성기 파일만 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-110">Only the Report Builder files are removed.</span></span>  
  
### <a name="to-uninstall-report-builder-from-the-control-panel"></a><span data-ttu-id="bf77a-111">제어판에서 보고서 작성기를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="bf77a-111">To uninstall Report Builder from the control panel</span></span>  
  
1.  <span data-ttu-id="bf77a-112">**시작** 메뉴에서 **제어판**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-112">On the **Start** menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="bf77a-113">제어판에서 **프로그램 및 기능**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-113">In the Control Panel, click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="bf77a-114">**이름** 목록에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 보고서 작성기를 찾아 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-114">Locate [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Builder in the **Name** list and click it.</span></span>  
  
4.  <span data-ttu-id="bf77a-115">**제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-115">Click **Uninstall**.</span></span>  
  
5.  <span data-ttu-id="bf77a-116">보고서 작성기를 제거할지 묻는 메시지가 표시되면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-116">If prompted to confirm the uninstall of Report Builder, click **Yes**.</span></span>  
  
### <a name="to-uninstall-report-builder-from-the-command-line"></a><span data-ttu-id="bf77a-117">명령줄에서 보고서 작성기를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="bf77a-117">To uninstall Report Builder from the command line</span></span>  
  
1.  <span data-ttu-id="bf77a-118">**시작** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-118">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="bf77a-119">**열기** 입력란에 다음을 입력 합니다.`cmd.`</span><span class="sxs-lookup"><span data-stu-id="bf77a-119">In the **Open** text box, type `cmd.`</span></span>  
  
3.  <span data-ttu-id="bf77a-120">명령 프롬프트 창에서 ReportBuilder3_x86.msi가 있는 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-120">In the command prompt window, navigate to the folder with ReportBuilder3_x86.msi.</span></span>  
  
4.  <span data-ttu-id="bf77a-121">다음과 같은 기본 명령줄을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-121">Type a basic command line such as the following:</span></span>  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v install.log`  
  
 <span data-ttu-id="bf77a-122">로깅을 포함할 수 있는 경우 다음과 같은 명령줄을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-122">If you can to include logging, use a command line such as the following:</span></span>  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v c:\junk\install.log`  
  
1.  <span data-ttu-id="bf77a-123">**Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="bf77a-123">Press **Enter**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf77a-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf77a-124">See Also</span></span>  
 <span data-ttu-id="bf77a-125">[설치, 제거 및 보고서 작성기 지원](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="bf77a-125">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 [<span data-ttu-id="bf77a-126">독립 실행형 버전의 보고서 작성기 &#40;보고서 작성기를 설치&#41;</span><span class="sxs-lookup"><span data-stu-id="bf77a-126">Install the Stand-Alone Version of Report Builder &#40;Report Builder&#41;</span></span>](install-report-builder.md)  
  
  
