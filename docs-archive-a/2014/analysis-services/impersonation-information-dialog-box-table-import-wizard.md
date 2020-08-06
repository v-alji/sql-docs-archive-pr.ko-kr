---
title: 가장 정보 대화 상자 (테이블 가져오기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5300f8b6106a7f29f51018b4e039c2a8c28aa729
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728927"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a><span data-ttu-id="42706-102">가장 정보 대화 상자(테이블 가져오기 마법사)</span><span class="sxs-lookup"><span data-stu-id="42706-102">Impersonation Information Dialog Box (Table Import Wizard)</span></span>
  <span data-ttu-id="42706-103">**가장 정보** 페이지를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 데이터 원본에 연결하는 데 사용할 자격 증명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42706-103">Use the **Impersonation Information** page to specify the credentials that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] will use to connect to the data source.</span></span> <span data-ttu-id="42706-104">자격 증명 가장에 대 한 자세한 내용은 [가장 &#40;SSAS 테이블 형식&#41;](tabular-models/impersonation-ssas-tabular.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42706-104">For more information about credentials impersonation, see [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="42706-105">옵션</span><span class="sxs-lookup"><span data-stu-id="42706-105">Options</span></span>  
 <span data-ttu-id="42706-106">**특정 Windows 사용자 이름 및 암호**</span><span class="sxs-lookup"><span data-stu-id="42706-106">**Specific Windows user name and password**</span></span>  
 <span data-ttu-id="42706-107">지정된 Windows 사용자 계정의 보안 자격 증명을 테이블 형식 모델에 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42706-107">Select this option to have the tabular model use the security credentials of a specified Windows user account.</span></span>  
  
 <span data-ttu-id="42706-108">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="42706-108">**User name**</span></span>  
 <span data-ttu-id="42706-109">사용할 사용자 계정의 도메인과 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="42706-109">Type the domain and name of the user account to be used.</span></span> <span data-ttu-id="42706-110">이때 다음 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42706-110">Use the following format:</span></span>  
  
 <span data-ttu-id="42706-111">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="42706-111">*\<Domain name>* **\\** *\<User account name>*</span></span>  
  
 <span data-ttu-id="42706-112">이 옵션은 **특정 사용자 이름 및 암호 사용** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42706-112">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="42706-113">**암호**</span><span class="sxs-lookup"><span data-stu-id="42706-113">**Password**</span></span>  
 <span data-ttu-id="42706-114">테이블 형식 모델에서 사용할 사용자 계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="42706-114">Type the password of the user account to be used by the Tabular model.</span></span>  
  
 <span data-ttu-id="42706-115">이 옵션은 **특정 사용자 이름 및 암호 사용** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42706-115">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="42706-116">**서비스 계정**</span><span class="sxs-lookup"><span data-stu-id="42706-116">**Service account**</span></span>  
 <span data-ttu-id="42706-117">모델을 관리하는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서비스와 연결된 보안 자격 증명을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42706-117">Select this option to use the security credentials associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] service that manages the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42706-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42706-118">See Also</span></span>  
 [<span data-ttu-id="42706-119">가장&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="42706-119">Impersonation &#40;SSAS Tabular&#41;</span></span>](tabular-models/impersonation-ssas-tabular.md)  
  
  
