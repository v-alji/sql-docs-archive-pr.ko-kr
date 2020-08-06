---
title: 데이터 뷰어 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataviewer.f1
helpviewer_keywords:
- Data Viewer dialog box
ms.assetid: 6351309a-688f-4e82-9697-1712130f10a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dc576981e875eade84dd3576f4ed93b66784411f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651818"
---
# <a name="data-viewer"></a><span data-ttu-id="85176-102">데이터 뷰어</span><span class="sxs-lookup"><span data-stu-id="85176-102">Data Viewer</span></span>
  <span data-ttu-id="85176-103">경로에서 데이터 뷰어를 사용하도록 구성한 경우 데이터 뷰어에서는 데이터가 두 데이터 흐름 구성 요소 간을 이동할 때 데이터를 버퍼별로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="85176-103">If a path is configured to use a data viewer, the Data Viewer displays the data buffer by buffer as data moves between two data flow components.</span></span>  
  
## <a name="options"></a><span data-ttu-id="85176-104">옵션</span><span class="sxs-lookup"><span data-stu-id="85176-104">Options</span></span>  
 <span data-ttu-id="85176-105">**녹색 화살표**</span><span class="sxs-lookup"><span data-stu-id="85176-105">**Green arrow**</span></span>  
 <span data-ttu-id="85176-106">다음 버퍼에 데이터를 표시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85176-106">Click to display the data in the next buffer.</span></span> <span data-ttu-id="85176-107">데이터를 단일 버퍼로 이동할 수 있는 경우 이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85176-107">If the data can be moved in a single buffer, this option is not available.</span></span>  
  
 <span data-ttu-id="85176-108">**분리**</span><span class="sxs-lookup"><span data-stu-id="85176-108">**Detach**</span></span>  
 <span data-ttu-id="85176-109">데이터 뷰어를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="85176-109">Detach the data viewer.</span></span>  
  
 <span data-ttu-id="85176-110">**참고** 데이터 뷰어를 분리해도 데이터 뷰어가 삭제되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85176-110">**Note** Detaching a data viewer does not delete the data viewer.</span></span> <span data-ttu-id="85176-111">데이터 뷰어를 분리한 경우 데이터는 계속해서 경로를 통해 전달되지만 뷰어의 데이터는 각 버퍼의 데이터와 일치하도록 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85176-111">If the data viewer has been detached, data continues to flow through the path, but the data in the viewer is not updated to match the data in each buffer.</span></span>  
  
 <span data-ttu-id="85176-112">**연결**</span><span class="sxs-lookup"><span data-stu-id="85176-112">**Attach**</span></span>  
 <span data-ttu-id="85176-113">데이터 뷰어를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="85176-113">Attach a data viewer.</span></span>  
  
 <span data-ttu-id="85176-114">**참고** 데이터 뷰어를 연결하면 뷰어에서 데이터 흐름에 있는 각 버퍼의 정보를 표시한 다음 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="85176-114">**Note** When the data viewer is attached, it displays information from each buffer in the data flow and then pauses.</span></span> <span data-ttu-id="85176-115">녹색 화살표를 사용하여 버퍼 내에서 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85176-115">You can advance through the buffers by using the green arrow.</span></span>  
  
 <span data-ttu-id="85176-116">**데이터 복사**</span><span class="sxs-lookup"><span data-stu-id="85176-116">**Copy Data**</span></span>  
 <span data-ttu-id="85176-117">현재 버퍼의 데이터를 클립보드로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="85176-117">Copy data in the current buffer to the Clipboard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85176-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85176-118">See Also</span></span>  
 [<span data-ttu-id="85176-119">데이터 흐름 디버깅</span><span class="sxs-lookup"><span data-stu-id="85176-119">Debugging Data Flow</span></span>](../troubleshooting/debugging-data-flow.md)  
  
  
