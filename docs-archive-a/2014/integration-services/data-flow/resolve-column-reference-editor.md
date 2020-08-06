---
title: 열 참조 확인 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.resolvereferences.mapper.F1
- sql12.dts.designer.resolvereferences.preview.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 600b6f4d5ec12290d654f0854cc548a5bbcf4335
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651814"
---
# <a name="resolve-column-reference-editor"></a><span data-ttu-id="b60ae-102">열 참조 확인 편집기</span><span class="sxs-lookup"><span data-stu-id="b60ae-102">Resolve Column Reference Editor</span></span>
  <span data-ttu-id="b60ae-103">입력 경로의 연결이 끊어졌거나 경로에 매핑되지 않은 열이 있는 경우 해당 데이터 경로 옆에 오류 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b60ae-103">When an input path is disconnected or if there are any unmapped columns in the path, an error icon is displayed beside the corresponding data path.</span></span> <span data-ttu-id="b60ae-104">열 참조 오류 확인을 간소화하기 위해 새 참조 확인 편집기가 실행 트리의 모든 경로에 대해 매핑되지 않은 출력 열과 매핑되지 않은 입력 열을 연결하도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b60ae-104">To simplify the resolution of column reference errors, the new Resolve References editor allows you to link unmapped output columns with unmapped input columns for all paths in the execution tree.</span></span> <span data-ttu-id="b60ae-105">참조 확인 편집기는 또한 확인 중인 경로를 나타내기 위해 해당 경로를 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b60ae-105">The Resolve References editor will also highlight the paths to indicate which paths are being resolved.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b60ae-106">이제 입력 경로의 연결이 끊긴 경우에도 구성 요소를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b60ae-106">It is now possible to edit a component even when its input path is disconnected</span></span>  
  
 <span data-ttu-id="b60ae-107">모든 열 참조가 확인된 후 다른 데이터 경로 오류가 없으면 데이터 경로 옆에 오류 아이콘이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b60ae-107">After all column references have been resolved, if there are no other data path errors, no error icons will be displayed beside the data paths.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b60ae-108">옵션</span><span class="sxs-lookup"><span data-stu-id="b60ae-108">Options</span></span>  
 <span data-ttu-id="b60ae-109">매핑되지 않은 출력 열(원본):</span><span class="sxs-lookup"><span data-stu-id="b60ae-109">Unmapped Output Columns (Source):</span></span>  
 <span data-ttu-id="b60ae-110">현재 매핑되지 않은 업스트림 경로의 열</span><span class="sxs-lookup"><span data-stu-id="b60ae-110">Columns from the upstream path that are not currently mapped</span></span>  
  
 <span data-ttu-id="b60ae-111">매핑된 열(원본):</span><span class="sxs-lookup"><span data-stu-id="b60ae-111">Mapped Columns (Source):</span></span>  
 <span data-ttu-id="b60ae-112">다운스트림 경로의 열에 매핑된 업스트림 경로의 열</span><span class="sxs-lookup"><span data-stu-id="b60ae-112">Columns from the upstream path that are mapped to columns from the downstream path</span></span>  
  
 <span data-ttu-id="b60ae-113">매핑된 열(대상):</span><span class="sxs-lookup"><span data-stu-id="b60ae-113">Mapped Columns (Destination):</span></span>  
 <span data-ttu-id="b60ae-114">다운스트림 경로의 열에 매핑된 업스트림 경로의 열</span><span class="sxs-lookup"><span data-stu-id="b60ae-114">Columns from the upstream path that are mapped to columns from the downstream path</span></span>  
  
 <span data-ttu-id="b60ae-115">매핑되지 않은 입력 열(대상):</span><span class="sxs-lookup"><span data-stu-id="b60ae-115">Unmapped Input Columns (Destination):</span></span>  
 <span data-ttu-id="b60ae-116">현재 매핑되지 않은 다운스트림 경로의 열</span><span class="sxs-lookup"><span data-stu-id="b60ae-116">Columns from the downstream path that are not currently mapped</span></span>  
  
 <span data-ttu-id="b60ae-117">매핑되지 않은 입력 열 삭제</span><span class="sxs-lookup"><span data-stu-id="b60ae-117">Delete Unmapped Input Columns</span></span>  
 <span data-ttu-id="b60ae-118">데이터 경로 대상에서 매핑되지 않은 열을 무시하려면 매핑되지 않은 입력 열 삭제를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b60ae-118">Check Delete Unmapped Input Columns to ignore unmapped columns at the destination of the data path.</span></span> <span data-ttu-id="b60ae-119">변경 내용 미리 보기 단추를 클릭하면 확인 단추를 누를 경우 적용되는 변경 내용 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b60ae-119">The Preview Changes button displays a list of the changes that will occur when you press the OK button.</span></span>  
  
  
