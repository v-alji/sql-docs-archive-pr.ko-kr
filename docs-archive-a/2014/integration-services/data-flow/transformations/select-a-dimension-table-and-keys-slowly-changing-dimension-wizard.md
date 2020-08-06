---
title: 차원 테이블 및 키 선택(느린 변경 차원 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 671c66a8a5d5f1f4f5201fd8c9ecc144540d8b68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743400"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a><span data-ttu-id="5d5e3-102">차원 테이블 및 키 선택(느린 변경 차원 마법사)</span><span class="sxs-lookup"><span data-stu-id="5d5e3-102">Select a Dimension Table and Keys (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="5d5e3-103">**차원 테이블 및 키 선택** 페이지를 사용하여 로드할 차원 테이블을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-103">Use the **Select a Dimension Table and Keys** page to select a dimension table to load.</span></span> <span data-ttu-id="5d5e3-104">데이터 흐름의 열을 로드하는 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-104">Map columns from the data flow to the columns that will be loaded.</span></span>  
  
 <span data-ttu-id="5d5e3-105">이 마법사에 대한 자세한 내용은 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-105">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5d5e3-106">옵션</span><span class="sxs-lookup"><span data-stu-id="5d5e3-106">Options</span></span>  
 <span data-ttu-id="5d5e3-107">**Connection manager**</span><span class="sxs-lookup"><span data-stu-id="5d5e3-107">**Connection manager**</span></span>  
 <span data-ttu-id="5d5e3-108">목록에서 기존 OLE DB 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 OLE DB 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-108">Select an existing OLE DB connection manager from the list, or click **New** to create an OLE DB connection manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d5e3-109">느린 변경 차원 마법사에서는 OLE DB 연결 관리자만 지원하며 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 대한 연결만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-109">The Slowly Changing Dimension Wizard only supports OLE DB connection managers, and only supports connections to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5d5e3-110">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="5d5e3-110">**New**</span></span>  
 <span data-ttu-id="5d5e3-111">**OLE DB 연결 관리자 구성** 대화 상자를 사용하여 기존 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 OLE DB 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-111">Use the **Configure OLE DB Connection Manager** dialog box to select an existing connection manager, or click **New** to create a new OLE DB connection.</span></span>  
  
 <span data-ttu-id="5d5e3-112">**테이블 또는 뷰**</span><span class="sxs-lookup"><span data-stu-id="5d5e3-112">**Table or View**</span></span>  
 <span data-ttu-id="5d5e3-113">목록에서 테이블이나 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-113">Select a table or view from the list.</span></span>  
  
 <span data-ttu-id="5d5e3-114">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="5d5e3-114">**Input Columns**</span></span>  
 <span data-ttu-id="5d5e3-115">입력 열 목록에서 매핑을 지정할 입력 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-115">Select from the list of input columns for which you may specify mapping.</span></span>  
  
 <span data-ttu-id="5d5e3-116">**차원 열**</span><span class="sxs-lookup"><span data-stu-id="5d5e3-116">**Dimension Columns**</span></span>  
 <span data-ttu-id="5d5e3-117">사용 가능한 차원 열을 모두 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-117">View all available dimension columns.</span></span>  
  
 <span data-ttu-id="5d5e3-118">**키 유형**</span><span class="sxs-lookup"><span data-stu-id="5d5e3-118">**Key Type**</span></span>  
 <span data-ttu-id="5d5e3-119">차원 열 중 하나를 비즈니스 키로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-119">Select one of the dimension columns to be the business key.</span></span> <span data-ttu-id="5d5e3-120">비즈니스 키는 반드시 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d5e3-120">You must have one business key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d5e3-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d5e3-121">See Also</span></span>  
 [<span data-ttu-id="5d5e3-122">느린 변경 차원 마법사를 사용하여 출력 구성</span><span class="sxs-lookup"><span data-stu-id="5d5e3-122">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
