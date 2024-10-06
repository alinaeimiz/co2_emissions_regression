# co2_emissions_regression
<!DOCTYPE html>

<html lang="en">
<head><meta charset="utf-8"/>
<meta content="width=device-width, initial-scale=1.0" name="viewport"/>
<title>co2_emissions_linear_regression</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
<style type="text/css">
    pre { line-height: 125%; }
td.linenos .normal { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
span.linenos { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
td.linenos .special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
span.linenos.special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
.highlight .hll { background-color: var(--jp-cell-editor-active-background) }
.highlight { background: var(--jp-cell-editor-background); color: var(--jp-mirror-editor-variable-color) }
.highlight .c { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment */
.highlight .err { color: var(--jp-mirror-editor-error-color) } /* Error */
.highlight .k { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword */
.highlight .o { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator */
.highlight .p { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation */
.highlight .ch { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Multiline */
.highlight .cp { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Preproc */
.highlight .cpf { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Single */
.highlight .cs { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Special */
.highlight .kc { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Pseudo */
.highlight .kr { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Type */
.highlight .m { color: var(--jp-mirror-editor-number-color) } /* Literal.Number */
.highlight .s { color: var(--jp-mirror-editor-string-color) } /* Literal.String */
.highlight .ow { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator.Word */
.highlight .pm { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation.Marker */
.highlight .w { color: var(--jp-mirror-editor-variable-color) } /* Text.Whitespace */
.highlight .mb { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Bin */
.highlight .mf { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Float */
.highlight .mh { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Hex */
.highlight .mi { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer */
.highlight .mo { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Oct */
.highlight .sa { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Affix */
.highlight .sb { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Backtick */
.highlight .sc { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Char */
.highlight .dl { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Delimiter */
.highlight .sd { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Doc */
.highlight .s2 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Double */
.highlight .se { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Escape */
.highlight .sh { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Heredoc */
.highlight .si { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Interpol */
.highlight .sx { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Other */
.highlight .sr { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Regex */
.highlight .s1 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Single */
.highlight .ss { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Symbol */
.highlight .il { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer.Long */
  </style>
<style type="text/css">
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*
 * Mozilla scrollbar styling
 */

/* use standard opaque scrollbars for most nodes */
[data-jp-theme-scrollbars='true'] {
  scrollbar-color: rgb(var(--jp-scrollbar-thumb-color))
    var(--jp-scrollbar-background-color);
}

/* for code nodes, use a transparent style of scrollbar. These selectors
 * will match lower in the tree, and so will override the above */
[data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar,
[data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar {
  scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
}

/* tiny scrollbar */

.jp-scrollbar-tiny {
  scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
  scrollbar-width: thin;
}

/* tiny scrollbar */

.jp-scrollbar-tiny::-webkit-scrollbar,
.jp-scrollbar-tiny::-webkit-scrollbar-corner {
  background-color: transparent;
  height: 4px;
  width: 4px;
}

.jp-scrollbar-tiny::-webkit-scrollbar-thumb {
  background: rgba(var(--jp-scrollbar-thumb-color), 0.5);
}

.jp-scrollbar-tiny::-webkit-scrollbar-track:horizontal {
  border-left: 0 solid transparent;
  border-right: 0 solid transparent;
}

.jp-scrollbar-tiny::-webkit-scrollbar-track:vertical {
  border-top: 0 solid transparent;
  border-bottom: 0 solid transparent;
}

/*
 * Lumino
 */

.lm-ScrollBar[data-orientation='horizontal'] {
  min-height: 16px;
  max-height: 16px;
  min-width: 45px;
  border-top: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='vertical'] {
  min-width: 16px;
  max-width: 16px;
  min-height: 45px;
  border-left: 1px solid #a0a0a0;
}

.lm-ScrollBar-button {
  background-color: #f0f0f0;
  background-position: center center;
  min-height: 15px;
  max-height: 15px;
  min-width: 15px;
  max-width: 15px;
}

.lm-ScrollBar-button:hover {
  background-color: #dadada;
}

.lm-ScrollBar-button.lm-mod-active {
  background-color: #cdcdcd;
}

.lm-ScrollBar-track {
  background: #f0f0f0;
}

.lm-ScrollBar-thumb {
  background: #cdcdcd;
}

.lm-ScrollBar-thumb:hover {
  background: #bababa;
}

.lm-ScrollBar-thumb.lm-mod-active {
  background: #a0a0a0;
}

.lm-ScrollBar[data-orientation='horizontal'] .lm-ScrollBar-thumb {
  height: 100%;
  min-width: 15px;
  border-left: 1px solid #a0a0a0;
  border-right: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='vertical'] .lm-ScrollBar-thumb {
  width: 100%;
  min-height: 15px;
  border-top: 1px solid #a0a0a0;
  border-bottom: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='horizontal']
  .lm-ScrollBar-button[data-action='decrement'] {
  background-image: var(--jp-icon-caret-left);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='horizontal']
  .lm-ScrollBar-button[data-action='increment'] {
  background-image: var(--jp-icon-caret-right);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='vertical']
  .lm-ScrollBar-button[data-action='decrement'] {
  background-image: var(--jp-icon-caret-up);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='vertical']
  .lm-ScrollBar-button[data-action='increment'] {
  background-image: var(--jp-icon-caret-down);
  background-size: 17px;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-Widget {
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
}

.lm-Widget.lm-mod-hidden {
  display: none !important;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

.lm-AccordionPanel[data-orientation='horizontal'] > .lm-AccordionPanel-title {
  /* Title is rotated for horizontal accordion panel using CSS */
  display: block;
  transform-origin: top left;
  transform: rotate(-90deg) translate(-100%);
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-CommandPalette {
  display: flex;
  flex-direction: column;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.lm-CommandPalette-search {
  flex: 0 0 auto;
}

.lm-CommandPalette-content {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  min-height: 0;
  overflow: auto;
  list-style-type: none;
}

.lm-CommandPalette-header {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.lm-CommandPalette-item {
  display: flex;
  flex-direction: row;
}

.lm-CommandPalette-itemIcon {
  flex: 0 0 auto;
}

.lm-CommandPalette-itemContent {
  flex: 1 1 auto;
  overflow: hidden;
}

.lm-CommandPalette-itemShortcut {
  flex: 0 0 auto;
}

.lm-CommandPalette-itemLabel {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.lm-close-icon {
  border: 1px solid transparent;
  background-color: transparent;
  position: absolute;
  z-index: 1;
  right: 3%;
  top: 0;
  bottom: 0;
  margin: auto;
  padding: 7px 0;
  display: none;
  vertical-align: middle;
  outline: 0;
  cursor: pointer;
}
.lm-close-icon:after {
  content: 'X';
  display: block;
  width: 15px;
  height: 15px;
  text-align: center;
  color: #000;
  font-weight: normal;
  font-size: 12px;
  cursor: pointer;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-DockPanel {
  z-index: 0;
}

.lm-DockPanel-widget {
  z-index: 0;
}

.lm-DockPanel-tabBar {
  z-index: 1;
}

.lm-DockPanel-handle {
  z-index: 2;
}

.lm-DockPanel-handle.lm-mod-hidden {
  display: none !important;
}

.lm-DockPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}

.lm-DockPanel-handle[data-orientation='horizontal'] {
  cursor: ew-resize;
}

.lm-DockPanel-handle[data-orientation='vertical'] {
  cursor: ns-resize;
}

.lm-DockPanel-handle[data-orientation='horizontal']:after {
  left: 50%;
  min-width: 8px;
  transform: translateX(-50%);
}

.lm-DockPanel-handle[data-orientation='vertical']:after {
  top: 50%;
  min-height: 8px;
  transform: translateY(-50%);
}

.lm-DockPanel-overlay {
  z-index: 3;
  box-sizing: border-box;
  pointer-events: none;
}

.lm-DockPanel-overlay.lm-mod-hidden {
  display: none !important;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-Menu {
  z-index: 10000;
  position: absolute;
  white-space: nowrap;
  overflow-x: hidden;
  overflow-y: auto;
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.lm-Menu-content {
  margin: 0;
  padding: 0;
  display: table;
  list-style-type: none;
}

.lm-Menu-item {
  display: table-row;
}

.lm-Menu-item.lm-mod-hidden,
.lm-Menu-item.lm-mod-collapsed {
  display: none !important;
}

.lm-Menu-itemIcon,
.lm-Menu-itemSubmenuIcon {
  display: table-cell;
  text-align: center;
}

.lm-Menu-itemLabel {
  display: table-cell;
  text-align: left;
}

.lm-Menu-itemShortcut {
  display: table-cell;
  text-align: right;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-MenuBar {
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.lm-MenuBar-content {
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: row;
  list-style-type: none;
}

.lm-MenuBar-item {
  box-sizing: border-box;
}

.lm-MenuBar-itemIcon,
.lm-MenuBar-itemLabel {
  display: inline-block;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-ScrollBar {
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.lm-ScrollBar[data-orientation='horizontal'] {
  flex-direction: row;
}

.lm-ScrollBar[data-orientation='vertical'] {
  flex-direction: column;
}

.lm-ScrollBar-button {
  box-sizing: border-box;
  flex: 0 0 auto;
}

.lm-ScrollBar-track {
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
  flex: 1 1 auto;
}

.lm-ScrollBar-thumb {
  box-sizing: border-box;
  position: absolute;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-SplitPanel-child {
  z-index: 0;
}

.lm-SplitPanel-handle {
  z-index: 1;
}

.lm-SplitPanel-handle.lm-mod-hidden {
  display: none !important;
}

.lm-SplitPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}

.lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle {
  cursor: ew-resize;
}

.lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle {
  cursor: ns-resize;
}

.lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle:after {
  left: 50%;
  min-width: 8px;
  transform: translateX(-50%);
}

.lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle:after {
  top: 50%;
  min-height: 8px;
  transform: translateY(-50%);
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-TabBar {
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.lm-TabBar[data-orientation='horizontal'] {
  flex-direction: row;
  align-items: flex-end;
}

.lm-TabBar[data-orientation='vertical'] {
  flex-direction: column;
  align-items: flex-end;
}

.lm-TabBar-content {
  margin: 0;
  padding: 0;
  display: flex;
  flex: 1 1 auto;
  list-style-type: none;
}

.lm-TabBar[data-orientation='horizontal'] > .lm-TabBar-content {
  flex-direction: row;
}

.lm-TabBar[data-orientation='vertical'] > .lm-TabBar-content {
  flex-direction: column;
}

.lm-TabBar-tab {
  display: flex;
  flex-direction: row;
  box-sizing: border-box;
  overflow: hidden;
  touch-action: none; /* Disable native Drag/Drop */
}

.lm-TabBar-tabIcon,
.lm-TabBar-tabCloseIcon {
  flex: 0 0 auto;
}

.lm-TabBar-tabLabel {
  flex: 1 1 auto;
  overflow: hidden;
  white-space: nowrap;
}

.lm-TabBar-tabInput {
  user-select: all;
  width: 100%;
  box-sizing: border-box;
}

.lm-TabBar-tab.lm-mod-hidden {
  display: none !important;
}

.lm-TabBar-addButton.lm-mod-hidden {
  display: none !important;
}

.lm-TabBar.lm-mod-dragging .lm-TabBar-tab {
  position: relative;
}

.lm-TabBar.lm-mod-dragging[data-orientation='horizontal'] .lm-TabBar-tab {
  left: 0;
  transition: left 150ms ease;
}

.lm-TabBar.lm-mod-dragging[data-orientation='vertical'] .lm-TabBar-tab {
  top: 0;
  transition: top 150ms ease;
}

.lm-TabBar.lm-mod-dragging .lm-TabBar-tab.lm-mod-dragging {
  transition: none;
}

.lm-TabBar-tabLabel .lm-TabBar-tabInput {
  user-select: all;
  width: 100%;
  box-sizing: border-box;
  background: inherit;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-TabPanel-tabBar {
  z-index: 1;
}

.lm-TabPanel-stackedPanel {
  z-index: 0;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Collapse {
  display: flex;
  flex-direction: column;
  align-items: stretch;
}

.jp-Collapse-header {
  padding: 1px 12px;
  background-color: var(--jp-layout-color1);
  border-bottom: solid var(--jp-border-width) var(--jp-border-color2);
  color: var(--jp-ui-font-color1);
  cursor: pointer;
  display: flex;
  align-items: center;
  font-size: var(--jp-ui-font-size0);
  font-weight: 600;
  text-transform: uppercase;
  user-select: none;
}

.jp-Collapser-icon {
  height: 16px;
}

.jp-Collapse-header-collapsed .jp-Collapser-icon {
  transform: rotate(-90deg);
  margin: auto 0;
}

.jp-Collapser-title {
  line-height: 25px;
}

.jp-Collapse-contents {
  padding: 0 12px;
  background-color: var(--jp-layout-color1);
  color: var(--jp-ui-font-color1);
  overflow: auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensureUiComponents() in @jupyterlab/buildutils */

/**
 * (DEPRECATED) Support for consuming icons as CSS background images
 */

/* Icons urls */

:root {
  --jp-icon-add-above: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPGcgY2xpcC1wYXRoPSJ1cmwoI2NsaXAwXzEzN18xOTQ5MikiPgo8cGF0aCBjbGFzcz0ianAtaWNvbjMiIGQ9Ik00Ljc1IDQuOTMwNjZINi42MjVWNi44MDU2NkM2LjYyNSA3LjAxMTkxIDYuNzkzNzUgNy4xODA2NiA3IDcuMTgwNjZDNy4yMDYyNSA3LjE4MDY2IDcuMzc1IDcuMDExOTEgNy4zNzUgNi44MDU2NlY0LjkzMDY2SDkuMjVDOS40NTYyNSA0LjkzMDY2IDkuNjI1IDQuNzYxOTEgOS42MjUgNC41NTU2NkM5LjYyNSA0LjM0OTQxIDkuNDU2MjUgNC4xODA2NiA5LjI1IDQuMTgwNjZINy4zNzVWMi4zMDU2NkM3LjM3NSAyLjA5OTQxIDcuMjA2MjUgMS45MzA2NiA3IDEuOTMwNjZDNi43OTM3NSAxLjkzMDY2IDYuNjI1IDIuMDk5NDEgNi42MjUgMi4zMDU2NlY0LjE4MDY2SDQuNzVDNC41NDM3NSA0LjE4MDY2IDQuMzc1IDQuMzQ5NDEgNC4zNzUgNC41NTU2NkM0LjM3NSA0Ljc2MTkxIDQuNTQzNzUgNC45MzA2NiA0Ljc1IDQuOTMwNjZaIiBmaWxsPSIjNjE2MTYxIiBzdHJva2U9IiM2MTYxNjEiIHN0cm9rZS13aWR0aD0iMC43Ii8+CjwvZz4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGNsaXAtcnVsZT0iZXZlbm9kZCIgZD0iTTExLjUgOS41VjExLjVMMi41IDExLjVWOS41TDExLjUgOS41Wk0xMiA4QzEyLjU1MjMgOCAxMyA4LjQ0NzcyIDEzIDlWMTJDMTMgMTIuNTUyMyAxMi41NTIzIDEzIDEyIDEzTDIgMTNDMS40NDc3MiAxMyAxIDEyLjU1MjMgMSAxMlY5QzEgOC40NDc3MiAxLjQ0NzcxIDggMiA4TDEyIDhaIiBmaWxsPSIjNjE2MTYxIi8+CjxkZWZzPgo8Y2xpcFBhdGggaWQ9ImNsaXAwXzEzN18xOTQ5MiI+CjxyZWN0IGNsYXNzPSJqcC1pY29uMyIgd2lkdGg9IjYiIGhlaWdodD0iNiIgZmlsbD0id2hpdGUiIHRyYW5zZm9ybT0ibWF0cml4KC0xIDAgMCAxIDEwIDEuNTU1NjYpIi8+CjwvY2xpcFBhdGg+CjwvZGVmcz4KPC9zdmc+Cg==);
  --jp-icon-add-below: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPGcgY2xpcC1wYXRoPSJ1cmwoI2NsaXAwXzEzN18xOTQ5OCkiPgo8cGF0aCBjbGFzcz0ianAtaWNvbjMiIGQ9Ik05LjI1IDEwLjA2OTNMNy4zNzUgMTAuMDY5M0w3LjM3NSA4LjE5NDM0QzcuMzc1IDcuOTg4MDkgNy4yMDYyNSA3LjgxOTM0IDcgNy44MTkzNEM2Ljc5Mzc1IDcuODE5MzQgNi42MjUgNy45ODgwOSA2LjYyNSA4LjE5NDM0TDYuNjI1IDEwLjA2OTNMNC43NSAxMC4wNjkzQzQuNTQzNzUgMTAuMDY5MyA0LjM3NSAxMC4yMzgxIDQuMzc1IDEwLjQ0NDNDNC4zNzUgMTAuNjUwNiA0LjU0Mzc1IDEwLjgxOTMgNC43NSAxMC44MTkzTDYuNjI1IDEwLjgxOTNMNi42MjUgMTIuNjk0M0M2LjYyNSAxMi45MDA2IDYuNzkzNzUgMTMuMDY5MyA3IDEzLjA2OTNDNy4yMDYyNSAxMy4wNjkzIDcuMzc1IDEyLjkwMDYgNy4zNzUgMTIuNjk0M0w3LjM3NSAxMC44MTkzTDkuMjUgMTAuODE5M0M5LjQ1NjI1IDEwLjgxOTMgOS42MjUgMTAuNjUwNiA5LjYyNSAxMC40NDQzQzkuNjI1IDEwLjIzODEgOS40NTYyNSAxMC4wNjkzIDkuMjUgMTAuMDY5M1oiIGZpbGw9IiM2MTYxNjEiIHN0cm9rZT0iIzYxNjE2MSIgc3Ryb2tlLXdpZHRoPSIwLjciLz4KPC9nPgo8cGF0aCBjbGFzcz0ianAtaWNvbjMiIGZpbGwtcnVsZT0iZXZlbm9kZCIgY2xpcC1ydWxlPSJldmVub2RkIiBkPSJNMi41IDUuNUwyLjUgMy41TDExLjUgMy41TDExLjUgNS41TDIuNSA1LjVaTTIgN0MxLjQ0NzcyIDcgMSA2LjU1MjI4IDEgNkwxIDNDMSAyLjQ0NzcyIDEuNDQ3NzIgMiAyIDJMMTIgMkMxMi41NTIzIDIgMTMgMi40NDc3MiAxMyAzTDEzIDZDMTMgNi41NTIyOSAxMi41NTIzIDcgMTIgN0wyIDdaIiBmaWxsPSIjNjE2MTYxIi8+CjxkZWZzPgo8Y2xpcFBhdGggaWQ9ImNsaXAwXzEzN18xOTQ5OCI+CjxyZWN0IGNsYXNzPSJqcC1pY29uMyIgd2lkdGg9IjYiIGhlaWdodD0iNiIgZmlsbD0id2hpdGUiIHRyYW5zZm9ybT0ibWF0cml4KDEgMS43NDg0NmUtMDcgMS43NDg0NmUtMDcgLTEgNCAxMy40NDQzKSIvPgo8L2NsaXBQYXRoPgo8L2RlZnM+Cjwvc3ZnPgo=);
  --jp-icon-add: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDEzaC02djZoLTJ2LTZINXYtMmg2VjVoMnY2aDZ2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-bell: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE2IDE2IiB2ZXJzaW9uPSIxLjEiPgogICA8cGF0aCBjbGFzcz0ianAtaWNvbjIganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMzMzMzMzIgogICAgICBkPSJtOCAwLjI5Yy0xLjQgMC0yLjcgMC43My0zLjYgMS44LTEuMiAxLjUtMS40IDMuNC0xLjUgNS4yLTAuMTggMi4yLTAuNDQgNC0yLjMgNS4zbDAuMjggMS4zaDVjMC4wMjYgMC42NiAwLjMyIDEuMSAwLjcxIDEuNSAwLjg0IDAuNjEgMiAwLjYxIDIuOCAwIDAuNTItMC40IDAuNi0xIDAuNzEtMS41aDVsMC4yOC0xLjNjLTEuOS0wLjk3LTIuMi0zLjMtMi4zLTUuMy0wLjEzLTEuOC0wLjI2LTMuNy0xLjUtNS4yLTAuODUtMS0yLjItMS44LTMuNi0xLjh6bTAgMS40YzAuODggMCAxLjkgMC41NSAyLjUgMS4zIDAuODggMS4xIDEuMSAyLjcgMS4yIDQuNCAwLjEzIDEuNyAwLjIzIDMuNiAxLjMgNS4yaC0xMGMxLjEtMS42IDEuMi0zLjQgMS4zLTUuMiAwLjEzLTEuNyAwLjMtMy4zIDEuMi00LjQgMC41OS0wLjcyIDEuNi0xLjMgMi41LTEuM3ptLTAuNzQgMTJoMS41Yy0wLjAwMTUgMC4yOCAwLjAxNSAwLjc5LTAuNzQgMC43OS0wLjczIDAuMDAxNi0wLjcyLTAuNTMtMC43NC0wLjc5eiIgLz4KPC9zdmc+Cg==);
  --jp-icon-bug-dot: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiPgogICAgICAgIDxwYXRoIGZpbGwtcnVsZT0iZXZlbm9kZCIgY2xpcC1ydWxlPSJldmVub2RkIiBkPSJNMTcuMTkgOEgyMFYxMEgxNy45MUMxNy45NiAxMC4zMyAxOCAxMC42NiAxOCAxMVYxMkgyMFYxNEgxOC41SDE4VjE0LjAyNzVDMTUuNzUgMTQuMjc2MiAxNCAxNi4xODM3IDE0IDE4LjVDMTQgMTkuMjA4IDE0LjE2MzUgMTkuODc3OSAxNC40NTQ5IDIwLjQ3MzlDMTMuNzA2MyAyMC44MTE3IDEyLjg3NTcgMjEgMTIgMjFDOS43OCAyMSA3Ljg1IDE5Ljc5IDYuODEgMThINFYxNkg2LjA5QzYuMDQgMTUuNjcgNiAxNS4zNCA2IDE1VjE0SDRWMTJINlYxMUM2IDEwLjY2IDYuMDQgMTAuMzMgNi4wOSAxMEg0VjhINi44MUM3LjI2IDcuMjIgNy44OCA2LjU1IDguNjIgNi4wNEw3IDQuNDFMOC40MSAzTDEwLjU5IDUuMTdDMTEuMDQgNS4wNiAxMS41MSA1IDEyIDVDMTIuNDkgNSAxMi45NiA1LjA2IDEzLjQyIDUuMTdMMTUuNTkgM0wxNyA0LjQxTDE1LjM3IDYuMDRDMTYuMTIgNi41NSAxNi43NCA3LjIyIDE3LjE5IDhaTTEwIDE2SDE0VjE0SDEwVjE2Wk0xMCAxMkgxNFYxMEgxMFYxMloiIGZpbGw9IiM2MTYxNjEiLz4KICAgICAgICA8cGF0aCBkPSJNMjIgMTguNUMyMiAyMC40MzMgMjAuNDMzIDIyIDE4LjUgMjJDMTYuNTY3IDIyIDE1IDIwLjQzMyAxNSAxOC41QzE1IDE2LjU2NyAxNi41NjcgMTUgMTguNSAxNUMyMC40MzMgMTUgMjIgMTYuNTY3IDIyIDE4LjVaIiBmaWxsPSIjNjE2MTYxIi8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-bug: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0yMCA4aC0yLjgxYy0uNDUtLjc4LTEuMDctMS40NS0xLjgyLTEuOTZMMTcgNC40MSAxNS41OSAzbC0yLjE3IDIuMTdDMTIuOTYgNS4wNiAxMi40OSA1IDEyIDVjLS40OSAwLS45Ni4wNi0xLjQxLjE3TDguNDEgMyA3IDQuNDFsMS42MiAxLjYzQzcuODggNi41NSA3LjI2IDcuMjIgNi44MSA4SDR2MmgyLjA5Yy0uMDUuMzMtLjA5LjY2LS4wOSAxdjFINHYyaDJ2MWMwIC4zNC4wNC42Ny4wOSAxSDR2MmgyLjgxYzEuMDQgMS43OSAyLjk3IDMgNS4xOSAzczQuMTUtMS4yMSA1LjE5LTNIMjB2LTJoLTIuMDljLjA1LS4zMy4wOS0uNjYuMDktMXYtMWgydi0yaC0ydi0xYzAtLjM0LS4wNC0uNjctLjA5LTFIMjBWOHptLTYgOGgtNHYtMmg0djJ6bTAtNGgtNHYtMmg0djJ6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-build: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE0LjkgMTcuNDVDMTYuMjUgMTcuNDUgMTcuMzUgMTYuMzUgMTcuMzUgMTVDMTcuMzUgMTMuNjUgMTYuMjUgMTIuNTUgMTQuOSAxMi41NUMxMy41NCAxMi41NSAxMi40NSAxMy42NSAxMi40NSAxNUMxMi40NSAxNi4zNSAxMy41NCAxNy40NSAxNC45IDE3LjQ1Wk0yMC4xIDE1LjY4TDIxLjU4IDE2Ljg0QzIxLjcxIDE2Ljk1IDIxLjc1IDE3LjEzIDIxLjY2IDE3LjI5TDIwLjI2IDE5LjcxQzIwLjE3IDE5Ljg2IDIwIDE5LjkyIDE5LjgzIDE5Ljg2TDE4LjA5IDE5LjE2QzE3LjczIDE5LjQ0IDE3LjMzIDE5LjY3IDE2LjkxIDE5Ljg1TDE2LjY0IDIxLjdDMTYuNjIgMjEuODcgMTYuNDcgMjIgMTYuMyAyMkgxMy41QzEzLjMyIDIyIDEzLjE4IDIxLjg3IDEzLjE1IDIxLjdMMTIuODkgMTkuODVDMTIuNDYgMTkuNjcgMTIuMDcgMTkuNDQgMTEuNzEgMTkuMTZMOS45NjAwMiAxOS44NkM5LjgxMDAyIDE5LjkyIDkuNjIwMDIgMTkuODYgOS41NDAwMiAxOS43MUw4LjE0MDAyIDE3LjI5QzguMDUwMDIgMTcuMTMgOC4wOTAwMiAxNi45NSA4LjIyMDAyIDE2Ljg0TDkuNzAwMDIgMTUuNjhMOS42NTAwMSAxNUw5LjcwMDAyIDE0LjMxTDguMjIwMDIgMTMuMTZDOC4wOTAwMiAxMy4wNSA4LjA1MDAyIDEyLjg2IDguMTQwMDIgMTIuNzFMOS41NDAwMiAxMC4yOUM5LjYyMDAyIDEwLjEzIDkuODEwMDIgMTAuMDcgOS45NjAwMiAxMC4xM0wxMS43MSAxMC44NEMxMi4wNyAxMC41NiAxMi40NiAxMC4zMiAxMi44OSAxMC4xNUwxMy4xNSA4LjI4OTk4QzEzLjE4IDguMTI5OTggMTMuMzIgNy45OTk5OCAxMy41IDcuOTk5OThIMTYuM0MxNi40NyA3Ljk5OTk4IDE2LjYyIDguMTI5OTggMTYuNjQgOC4yODk5OEwxNi45MSAxMC4xNUMxNy4zMyAxMC4zMiAxNy43MyAxMC41NiAxOC4wOSAxMC44NEwxOS44MyAxMC4xM0MyMCAxMC4wNyAyMC4xNyAxMC4xMyAyMC4yNiAxMC4yOUwyMS42NiAxMi43MUMyMS43NSAxMi44NiAyMS43MSAxMy4wNSAyMS41OCAxMy4xNkwyMC4xIDE0LjMxTDIwLjE1IDE1TDIwLjEgMTUuNjhaIi8+CiAgICA8cGF0aCBkPSJNNy4zMjk2NiA3LjQ0NDU0QzguMDgzMSA3LjAwOTU0IDguMzM5MzIgNi4wNTMzMiA3LjkwNDMyIDUuMjk5ODhDNy40NjkzMiA0LjU0NjQzIDYuNTA4MSA0LjI4MTU2IDUuNzU0NjYgNC43MTY1NkM1LjM5MTc2IDQuOTI2MDggNS4xMjY5NSA1LjI3MTE4IDUuMDE4NDkgNS42NzU5NEM0LjkxMDA0IDYuMDgwNzEgNC45NjY4MiA2LjUxMTk4IDUuMTc2MzQgNi44NzQ4OEM1LjYxMTM0IDcuNjI4MzIgNi41NzYyMiA3Ljg3OTU0IDcuMzI5NjYgNy40NDQ1NFpNOS42NTcxOCA0Ljc5NTkzTDEwLjg2NzIgNC45NTE3OUMxMC45NjI4IDQuOTc3NDEgMTEuMDQwMiA1LjA3MTMzIDExLjAzODIgNS4xODc5M0wxMS4wMzg4IDYuOTg4OTNDMTEuMDQ1NSA3LjEwMDU0IDEwLjk2MTYgNy4xOTUxOCAxMC44NTUgNy4yMTA1NEw5LjY2MDAxIDcuMzgwODNMOS4yMzkxNSA4LjEzMTg4TDkuNjY5NjEgOS4yNTc0NUM5LjcwNzI5IDkuMzYyNzEgOS42NjkzNCA5LjQ3Njk5IDkuNTc0MDggOS41MzE5OUw4LjAxNTIzIDEwLjQzMkM3LjkxMTMxIDEwLjQ5MiA3Ljc5MzM3IDEwLjQ2NzcgNy43MjEwNSAxMC4zODI0TDYuOTg3NDggOS40MzE4OEw2LjEwOTMxIDkuNDMwODNMNS4zNDcwNCAxMC4zOTA1QzUuMjg5MDkgMTAuNDcwMiA1LjE3MzgzIDEwLjQ5MDUgNS4wNzE4NyAxMC40MzM5TDMuNTEyNDUgOS41MzI5M0MzLjQxMDQ5IDkuNDc2MzMgMy4zNzY0NyA5LjM1NzQxIDMuNDEwNzUgOS4yNTY3OUwzLjg2MzQ3IDguMTQwOTNMMy42MTc0OSA3Ljc3NDg4TDMuNDIzNDcgNy4zNzg4M0wyLjIzMDc1IDcuMjEyOTdDMi4xMjY0NyA3LjE5MjM1IDIuMDQwNDkgNy4xMDM0MiAyLjA0MjQ1IDYuOTg2ODJMMi4wNDE4NyA1LjE4NTgyQzIuMDQzODMgNS4wNjkyMiAyLjExOTA5IDQuOTc5NTggMi4yMTcwNCA0Ljk2OTIyTDMuNDIwNjUgNC43OTM5M0wzLjg2NzQ5IDQuMDI3ODhMMy40MTEwNSAyLjkxNzMxQzMuMzczMzcgMi44MTIwNCAzLjQxMTMxIDIuNjk3NzYgMy41MTUyMyAyLjYzNzc2TDUuMDc0MDggMS43Mzc3NkM1LjE2OTM0IDEuNjgyNzYgNS4yODcyOSAxLjcwNzA0IDUuMzU5NjEgMS43OTIzMUw2LjExOTE1IDIuNzI3ODhMNi45ODAwMSAyLjczODkzTDcuNzI0OTYgMS43ODkyMkM3Ljc5MTU2IDEuNzA0NTggNy45MTU0OCAxLjY3OTIyIDguMDA4NzkgMS43NDA4Mkw5LjU2ODIxIDIuNjQxODJDOS42NzAxNyAyLjY5ODQyIDkuNzEyODUgMi44MTIzNCA5LjY4NzIzIDIuOTA3OTdMOS4yMTcxOCA0LjAzMzgzTDkuNDYzMTYgNC4zOTk4OEw5LjY1NzE4IDQuNzk1OTNaIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iOS45LDEzLjYgMy42LDcuNCA0LjQsNi42IDkuOSwxMi4yIDE1LjQsNi43IDE2LjEsNy40ICIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNS45TDksOS43bDMuOC0zLjhsMS4yLDEuMmwtNC45LDVsLTQuOS01TDUuMiw1Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNy41TDksMTEuMmwzLjgtMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-caret-left: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik0xMC44LDEyLjhMNy4xLDlsMy44LTMuOGwwLDcuNkgxMC44eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-caret-right: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik03LjIsNS4yTDEwLjksOWwtMy44LDMuOFY1LjJINy4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-caret-up-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iMTUuNCwxMy4zIDkuOSw3LjcgNC40LDEzLjIgMy42LDEyLjUgOS45LDYuMyAxNi4xLDEyLjYgIi8+Cgk8L2c+Cjwvc3ZnPgo=);
  --jp-icon-caret-up: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik01LjIsMTAuNUw5LDYuOGwzLjgsMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-case-sensitive: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgogIDxnIGNsYXNzPSJqcC1pY29uLWFjY2VudDIiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTcuNiw4aDAuOWwzLjUsOGgtMS4xTDEwLDE0SDZsLTAuOSwySDRMNy42LDh6IE04LDkuMUw2LjQsMTNoMy4yTDgsOS4xeiIvPgogICAgPHBhdGggZD0iTTE2LjYsOS44Yy0wLjIsMC4xLTAuNCwwLjEtMC43LDAuMWMtMC4yLDAtMC40LTAuMS0wLjYtMC4yYy0wLjEtMC4xLTAuMi0wLjQtMC4yLTAuNyBjLTAuMywwLjMtMC42LDAuNS0wLjksMC43Yy0wLjMsMC4xLTAuNywwLjItMS4xLDAuMmMtMC4zLDAtMC41LDAtMC43LTAuMWMtMC4yLTAuMS0wLjQtMC4yLTAuNi0wLjNjLTAuMi0wLjEtMC4zLTAuMy0wLjQtMC41IGMtMC4xLTAuMi0wLjEtMC40LTAuMS0wLjdjMC0wLjMsMC4xLTAuNiwwLjItMC44YzAuMS0wLjIsMC4zLTAuNCwwLjQtMC41QzEyLDcsMTIuMiw2LjksMTIuNSw2LjhjMC4yLTAuMSwwLjUtMC4xLDAuNy0wLjIgYzAuMy0wLjEsMC41LTAuMSwwLjctMC4xYzAuMiwwLDAuNC0wLjEsMC42LTAuMWMwLjIsMCwwLjMtMC4xLDAuNC0wLjJjMC4xLTAuMSwwLjItMC4yLDAuMi0wLjRjMC0xLTEuMS0xLTEuMy0xIGMtMC40LDAtMS40LDAtMS40LDEuMmgtMC45YzAtMC40LDAuMS0wLjcsMC4yLTFjMC4xLTAuMiwwLjMtMC40LDAuNS0wLjZjMC4yLTAuMiwwLjUtMC4zLDAuOC0wLjNDMTMuMyw0LDEzLjYsNCwxMy45LDQgYzAuMywwLDAuNSwwLDAuOCwwLjFjMC4zLDAsMC41LDAuMSwwLjcsMC4yYzAuMiwwLjEsMC40LDAuMywwLjUsMC41QzE2LDUsMTYsNS4yLDE2LDUuNnYyLjljMCwwLjIsMCwwLjQsMCwwLjUgYzAsMC4xLDAuMSwwLjIsMC4zLDAuMmMwLjEsMCwwLjIsMCwwLjMsMFY5Ljh6IE0xNS4yLDYuOWMtMS4yLDAuNi0zLjEsMC4yLTMuMSwxLjRjMCwxLjQsMy4xLDEsMy4xLTAuNVY2Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-check: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik05IDE2LjE3TDQuODMgMTJsLTEuNDIgMS40MUw5IDE5IDIxIDdsLTEuNDEtMS40MXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-circle-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDJDNi40NyAyIDIgNi40NyAyIDEyczQuNDcgMTAgMTAgMTAgMTAtNC40NyAxMC0xMFMxNy41MyAyIDEyIDJ6bTAgMThjLTQuNDEgMC04LTMuNTktOC04czMuNTktOCA4LTggOCAzLjU5IDggOC0zLjU5IDgtOCA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-circle: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iOSIgY3k9IjkiIHI9IjgiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-clear: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8bWFzayBpZD0iZG9udXRIb2xlIj4KICAgIDxyZWN0IHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgZmlsbD0id2hpdGUiIC8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSI4IiBmaWxsPSJibGFjayIvPgogIDwvbWFzaz4KCiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxyZWN0IGhlaWdodD0iMTgiIHdpZHRoPSIyIiB4PSIxMSIgeT0iMyIgdHJhbnNmb3JtPSJyb3RhdGUoMzE1LCAxMiwgMTIpIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIxMCIgbWFzaz0idXJsKCNkb251dEhvbGUpIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-close: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1ub25lIGpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIGpwLWljb24zLWhvdmVyIiBmaWxsPSJub25lIj4KICAgIDxjaXJjbGUgY3g9IjEyIiBjeT0iMTIiIHI9IjExIi8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIGpwLWljb24tYWNjZW50Mi1ob3ZlciIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMTkgNi40MUwxNy41OSA1IDEyIDEwLjU5IDYuNDEgNSA1IDYuNDEgMTAuNTkgMTIgNSAxNy41OSA2LjQxIDE5IDEyIDEzLjQxIDE3LjU5IDE5IDE5IDE3LjU5IDEzLjQxIDEyeiIvPgogIDwvZz4KCiAgPGcgY2xhc3M9ImpwLWljb24tbm9uZSBqcC1pY29uLWJ1c3kiIGZpbGw9Im5vbmUiPgogICAgPGNpcmNsZSBjeD0iMTIiIGN5PSIxMiIgcj0iNyIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-code-check: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBzaGFwZS1yZW5kZXJpbmc9Imdlb21ldHJpY1ByZWNpc2lvbiI+CiAgICA8cGF0aCBkPSJNNi41OSwzLjQxTDIsOEw2LjU5LDEyLjZMOCwxMS4xOEw0LjgyLDhMOCw0LjgyTDYuNTksMy40MU0xMi40MSwzLjQxTDExLDQuODJMMTQuMTgsOEwxMSwxMS4xOEwxMi40MSwxMi42TDE3LDhMMTIuNDEsMy40MU0yMS41OSwxMS41OUwxMy41LDE5LjY4TDkuODMsMTZMOC40MiwxNy40MUwxMy41LDIyLjVMMjMsMTNMMjEuNTksMTEuNTlaIiAvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-code: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTExLjQgMTguNkw2LjggMTRMMTEuNCA5LjRMMTAgOEw0IDE0TDEwIDIwTDExLjQgMTguNlpNMTYuNiAxOC42TDIxLjIgMTRMMTYuNiA5LjRMMTggOEwyNCAxNEwxOCAyMEwxNi42IDE4LjZWMTguNloiLz4KCTwvZz4KPC9zdmc+Cg==);
  --jp-icon-collapse-all: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGgKICAgICAgICAgICAgZD0iTTggMmMxIDAgMTEgMCAxMiAwczIgMSAyIDJjMCAxIDAgMTEgMCAxMnMwIDItMiAyQzIwIDE0IDIwIDQgMjAgNFMxMCA0IDYgNGMwLTIgMS0yIDItMnoiIC8+CiAgICAgICAgPHBhdGgKICAgICAgICAgICAgZD0iTTE4IDhjMC0xLTEtMi0yLTJTNSA2IDQgNnMtMiAxLTIgMmMwIDEgMCAxMSAwIDEyczEgMiAyIDJjMSAwIDExIDAgMTIgMHMyLTEgMi0yYzAtMSAwLTExIDAtMTJ6bS0yIDB2MTJINFY4eiIgLz4KICAgICAgICA8cGF0aCBkPSJNNiAxM3YyaDh2LTJ6IiAvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-console: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwMCAyMDAiPgogIDxnIGNsYXNzPSJqcC1jb25zb2xlLWljb24tYmFja2dyb3VuZC1jb2xvciBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMjg4RDEiPgogICAgPHBhdGggZD0iTTIwIDE5LjhoMTYwdjE1OS45SDIweiIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtY29uc29sZS1pY29uLWNvbG9yIGpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIiBmaWxsPSIjZmZmIj4KICAgIDxwYXRoIGQ9Ik0xMDUgMTI3LjNoNDB2MTIuOGgtNDB6TTUxLjEgNzdMNzQgOTkuOWwtMjMuMyAyMy4zIDEwLjUgMTAuNSAyMy4zLTIzLjNMOTUgOTkuOSA4NC41IDg5LjQgNjEuNiA2Ni41eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-copy: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTExLjksMUgzLjJDMi40LDEsMS43LDEuNywxLjcsMi41djEwLjJoMS41VjIuNWg4LjdWMXogTTE0LjEsMy45aC04Yy0wLjgsMC0xLjUsMC43LTEuNSwxLjV2MTAuMmMwLDAuOCwwLjcsMS41LDEuNSwxLjVoOCBjMC44LDAsMS41LTAuNywxLjUtMS41VjUuNEMxNS41LDQuNiwxNC45LDMuOSwxNC4xLDMuOXogTTE0LjEsMTUuNWgtOFY1LjRoOFYxNS41eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-copyright: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGVuYWJsZS1iYWNrZ3JvdW5kPSJuZXcgMCAwIDI0IDI0IiBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCI+CiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0xMS44OCw5LjE0YzEuMjgsMC4wNiwxLjYxLDEuMTUsMS42MywxLjY2aDEuNzljLTAuMDgtMS45OC0xLjQ5LTMuMTktMy40NS0zLjE5QzkuNjQsNy42MSw4LDksOCwxMi4xNCBjMCwxLjk0LDAuOTMsNC4yNCwzLjg0LDQuMjRjMi4yMiwwLDMuNDEtMS42NSwzLjQ0LTIuOTVoLTEuNzljLTAuMDMsMC41OS0wLjQ1LDEuMzgtMS42MywxLjQ0QzEwLjU1LDE0LjgzLDEwLDEzLjgxLDEwLDEyLjE0IEMxMCw5LjI1LDExLjI4LDkuMTYsMTEuODgsOS4xNHogTTEyLDJDNi40OCwyLDIsNi40OCwyLDEyczQuNDgsMTAsMTAsMTBzMTAtNC40OCwxMC0xMFMxNy41MiwyLDEyLDJ6IE0xMiwyMGMtNC40MSwwLTgtMy41OS04LTggczMuNTktOCw4LThzOCwzLjU5LDgsOFMxNi40MSwyMCwxMiwyMHoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-cut: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkuNjQgNy42NGMuMjMtLjUuMzYtMS4wNS4zNi0xLjY0IDAtMi4yMS0xLjc5LTQtNC00UzIgMy43OSAyIDZzMS43OSA0IDQgNGMuNTkgMCAxLjE0LS4xMyAxLjY0LS4zNkwxMCAxMmwtMi4zNiAyLjM2QzcuMTQgMTQuMTMgNi41OSAxNCA2IDE0Yy0yLjIxIDAtNCAxLjc5LTQgNHMxLjc5IDQgNCA0IDQtMS43OSA0LTRjMC0uNTktLjEzLTEuMTQtLjM2LTEuNjRMMTIgMTRsNyA3aDN2LTFMOS42NCA3LjY0ek02IDhjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTAgMTJjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTYtNy41Yy0uMjggMC0uNS0uMjItLjUtLjVzLjIyLS41LjUtLjUuNS4yMi41LjUtLjIyLjUtLjUuNXpNMTkgM2wtNiA2IDIgMiA3LTdWM3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-delete: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2cHgiIGhlaWdodD0iMTZweCI+CiAgICA8cGF0aCBkPSJNMCAwaDI0djI0SDB6IiBmaWxsPSJub25lIiAvPgogICAgPHBhdGggY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjI2MjYyIiBkPSJNNiAxOWMwIDEuMS45IDIgMiAyaDhjMS4xIDAgMi0uOSAyLTJWN0g2djEyek0xOSA0aC0zLjVsLTEtMWgtNWwtMSAxSDV2MmgxNFY0eiIgLz4KPC9zdmc+Cg==);
  --jp-icon-download: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDloLTRWM0g5djZINWw3IDcgNy03ek01IDE4djJoMTR2LTJINXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-duplicate: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGNsaXAtcnVsZT0iZXZlbm9kZCIgZD0iTTIuNzk5OTggMC44NzVIOC44OTU4MkM5LjIwMDYxIDAuODc1IDkuNDQ5OTggMS4xMzkxNCA5LjQ0OTk4IDEuNDYxOThDOS40NDk5OCAxLjc4NDgyIDkuMjAwNjEgMi4wNDg5NiA4Ljg5NTgyIDIuMDQ4OTZIMy4zNTQxNUMzLjA0OTM2IDIuMDQ4OTYgMi43OTk5OCAyLjMxMzEgMi43OTk5OCAyLjYzNTk0VjkuNjc5NjlDMi43OTk5OCAxMC4wMDI1IDIuNTUwNjEgMTAuMjY2NyAyLjI0NTgyIDEwLjI2NjdDMS45NDEwMyAxMC4yNjY3IDEuNjkxNjUgMTAuMDAyNSAxLjY5MTY1IDkuNjc5NjlWMi4wNDg5NkMxLjY5MTY1IDEuNDAzMjggMi4xOTA0IDAuODc1IDIuNzk5OTggMC44NzVaTTUuMzY2NjUgMTEuOVY0LjU1SDExLjA4MzNWMTEuOUg1LjM2NjY1Wk00LjE0MTY1IDQuMTQxNjdDNC4xNDE2NSAzLjY5MDYzIDQuNTA3MjggMy4zMjUgNC45NTgzMiAzLjMyNUgxMS40OTE3QzExLjk0MjcgMy4zMjUgMTIuMzA4MyAzLjY5MDYzIDEyLjMwODMgNC4xNDE2N1YxMi4zMDgzQzEyLjMwODMgMTIuNzU5NCAxMS45NDI3IDEzLjEyNSAxMS40OTE3IDEzLjEyNUg0Ljk1ODMyQzQuNTA3MjggMTMuMTI1IDQuMTQxNjUgMTIuNzU5NCA0LjE0MTY1IDEyLjMwODNWNC4xNDE2N1oiIGZpbGw9IiM2MTYxNjEiLz4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBkPSJNOS40MzU3NCA4LjI2NTA3SDguMzY0MzFWOS4zMzY1QzguMzY0MzEgOS40NTQzNSA4LjI2Nzg4IDkuNTUwNzggOC4xNTAwMiA5LjU1MDc4QzguMDMyMTcgOS41NTA3OCA3LjkzNTc0IDkuNDU0MzUgNy45MzU3NCA5LjMzNjVWOC4yNjUwN0g2Ljg2NDMxQzYuNzQ2NDUgOC4yNjUwNyA2LjY1MDAyIDguMTY4NjQgNi42NTAwMiA4LjA1MDc4QzYuNjUwMDIgNy45MzI5MiA2Ljc0NjQ1IDcuODM2NSA2Ljg2NDMxIDcuODM2NUg3LjkzNTc0VjYuNzY1MDdDNy45MzU3NCA2LjY0NzIxIDguMDMyMTcgNi41NTA3OCA4LjE1MDAyIDYuNTUwNzhDOC4yNjc4OCA2LjU1MDc4IDguMzY0MzEgNi42NDcyMSA4LjM2NDMxIDYuNzY1MDdWNy44MzY1SDkuNDM1NzRDOS41NTM2IDcuODM2NSA5LjY1MDAyIDcuOTMyOTIgOS42NTAwMiA4LjA1MDc4QzkuNjUwMDIgOC4xNjg2NCA5LjU1MzYgOC4yNjUwNyA5LjQzNTc0IDguMjY1MDdaIiBmaWxsPSIjNjE2MTYxIiBzdHJva2U9IiM2MTYxNjEiIHN0cm9rZS13aWR0aD0iMC41Ii8+Cjwvc3ZnPgo=);
  --jp-icon-edit: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMgMTcuMjVWMjFoMy43NUwxNy44MSA5Ljk0bC0zLjc1LTMuNzVMMyAxNy4yNXpNMjAuNzEgNy4wNGMuMzktLjM5LjM5LTEuMDIgMC0xLjQxbC0yLjM0LTIuMzRjLS4zOS0uMzktMS4wMi0uMzktMS40MSAwbC0xLjgzIDEuODMgMy43NSAzLjc1IDEuODMtMS44M3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-ellipses: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iNSIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxOSIgY3k9IjEyIiByPSIyIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-error: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj48Y2lyY2xlIGN4PSIxMiIgY3k9IjE5IiByPSIyIi8+PHBhdGggZD0iTTEwIDNoNHYxMmgtNHoiLz48L2c+CjxwYXRoIGZpbGw9Im5vbmUiIGQ9Ik0wIDBoMjR2MjRIMHoiLz4KPC9zdmc+Cg==);
  --jp-icon-expand-all: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGgKICAgICAgICAgICAgZD0iTTggMmMxIDAgMTEgMCAxMiAwczIgMSAyIDJjMCAxIDAgMTEgMCAxMnMwIDItMiAyQzIwIDE0IDIwIDQgMjAgNFMxMCA0IDYgNGMwLTIgMS0yIDItMnoiIC8+CiAgICAgICAgPHBhdGgKICAgICAgICAgICAgZD0iTTE4IDhjMC0xLTEtMi0yLTJTNSA2IDQgNnMtMiAxLTIgMmMwIDEgMCAxMSAwIDEyczEgMiAyIDJjMSAwIDExIDAgMTIgMHMyLTEgMi0yYzAtMSAwLTExIDAtMTJ6bS0yIDB2MTJINFY4eiIgLz4KICAgICAgICA8cGF0aCBkPSJNMTEgMTBIOXYzSDZ2MmgzdjNoMnYtM2gzdi0yaC0zeiIgLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-extension: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwLjUgMTFIMTlWN2MwLTEuMS0uOS0yLTItMmgtNFYzLjVDMTMgMi4xMiAxMS44OCAxIDEwLjUgMVM4IDIuMTIgOCAzLjVWNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAydjMuOEgzLjVjMS40OSAwIDIuNyAxLjIxIDIuNyAyLjdzLTEuMjEgMi43LTIuNyAyLjdIMlYyMGMwIDEuMS45IDIgMiAyaDMuOHYtMS41YzAtMS40OSAxLjIxLTIuNyAyLjctMi43IDEuNDkgMCAyLjcgMS4yMSAyLjcgMi43VjIySDE3YzEuMSAwIDItLjkgMi0ydi00aDEuNWMxLjM4IDAgMi41LTEuMTIgMi41LTIuNVMyMS44OCAxMSAyMC41IDExeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-fast-forward: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTQgMThsOC41LTZMNCA2djEyem05LTEydjEybDguNS02TDEzIDZ6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-file-upload: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkgMTZoNnYtNmg0bC03LTctNyA3aDR6bS00IDJoMTR2Mkg1eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-file: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuMyA4LjJsLTUuNS01LjVjLS4zLS4zLS43LS41LTEuMi0uNUgzLjljLS44LjEtMS42LjktMS42IDEuOHYxNC4xYzAgLjkuNyAxLjYgMS42IDEuNmgxNC4yYy45IDAgMS42LS43IDEuNi0xLjZWOS40Yy4xLS41LS4xLS45LS40LTEuMnptLTUuOC0zLjNsMy40IDMuNmgtMy40VjQuOXptMy45IDEyLjdINC43Yy0uMSAwLS4yIDAtLjItLjJWNC43YzAtLjIuMS0uMy4yLS4zaDcuMnY0LjRzMCAuOC4zIDEuMWMuMy4zIDEuMS4zIDEuMS4zaDQuM3Y3LjJzLS4xLjItLjIuMnoiLz4KPC9zdmc+Cg==);
  --jp-icon-filter-dot: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTE0LDEyVjE5Ljg4QzE0LjA0LDIwLjE4IDEzLjk0LDIwLjUgMTMuNzEsMjAuNzFDMTMuMzIsMjEuMSAxMi42OSwyMS4xIDEyLjMsMjAuNzFMMTAuMjksMTguN0MxMC4wNiwxOC40NyA5Ljk2LDE4LjE2IDEwLDE3Ljg3VjEySDkuOTdMNC4yMSw0LjYyQzMuODcsNC4xOSAzLjk1LDMuNTYgNC4zOCwzLjIyQzQuNTcsMy4wOCA0Ljc4LDMgNSwzVjNIMTlWM0MxOS4yMiwzIDE5LjQzLDMuMDggMTkuNjIsMy4yMkMyMC4wNSwzLjU2IDIwLjEzLDQuMTkgMTkuNzksNC42MkwxNC4wMywxMkgxNFoiIC8+CiAgPC9nPgogIDxnIGNsYXNzPSJqcC1pY29uLWRvdCIgZmlsbD0iI0ZGRiI+CiAgICA8Y2lyY2xlIGN4PSIxOCIgY3k9IjE3IiByPSIzIj48L2NpcmNsZT4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-filter-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEwIDE4aDR2LTJoLTR2MnpNMyA2djJoMThWNkgzem0zIDdoMTJ2LTJINnYyeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-filter: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTE0LDEyVjE5Ljg4QzE0LjA0LDIwLjE4IDEzLjk0LDIwLjUgMTMuNzEsMjAuNzFDMTMuMzIsMjEuMSAxMi42OSwyMS4xIDEyLjMsMjAuNzFMMTAuMjksMTguN0MxMC4wNiwxOC40NyA5Ljk2LDE4LjE2IDEwLDE3Ljg3VjEySDkuOTdMNC4yMSw0LjYyQzMuODcsNC4xOSAzLjk1LDMuNTYgNC4zOCwzLjIyQzQuNTcsMy4wOCA0Ljc4LDMgNSwzVjNIMTlWM0MxOS4yMiwzIDE5LjQzLDMuMDggMTkuNjIsMy4yMkMyMC4wNSwzLjU2IDIwLjEzLDQuMTkgMTkuNzksNC42MkwxNC4wMywxMkgxNFoiIC8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-folder-favorite: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjRweCIgdmlld0JveD0iMCAwIDI0IDI0IiB3aWR0aD0iMjRweCIgZmlsbD0iIzAwMDAwMCI+CiAgPHBhdGggZD0iTTAgMGgyNHYyNEgwVjB6IiBmaWxsPSJub25lIi8+PHBhdGggY2xhc3M9ImpwLWljb24zIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzYxNjE2MSIgZD0iTTIwIDZoLThsLTItMkg0Yy0xLjEgMC0yIC45LTIgMnYxMmMwIDEuMS45IDIgMiAyaDE2YzEuMSAwIDItLjkgMi0yVjhjMC0xLjEtLjktMi0yLTJ6bS0yLjA2IDExTDE1IDE1LjI4IDEyLjA2IDE3bC43OC0zLjMzLTIuNTktMi4yNCAzLjQxLS4yOUwxNSA4bDEuMzQgMy4xNCAzLjQxLjI5LTIuNTkgMi4yNC43OCAzLjMzeiIvPgo8L3N2Zz4K);
  --jp-icon-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY4YzAtMS4xLS45LTItMi0yaC04bC0yLTJ6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-home: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjRweCIgdmlld0JveD0iMCAwIDI0IDI0IiB3aWR0aD0iMjRweCIgZmlsbD0iIzAwMDAwMCI+CiAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPjxwYXRoIGNsYXNzPSJqcC1pY29uMyBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xMCAyMHYtNmg0djZoNXYtOGgzTDEyIDMgMiAxMmgzdjh6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-html5: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMDAiIGQ9Ik0xMDguNCAwaDIzdjIyLjhoMjEuMlYwaDIzdjY5aC0yM1Y0NmgtMjF2MjNoLTIzLjJNMjA2IDIzaC0yMC4zVjBoNjMuN3YyM0gyMjl2NDZoLTIzbTUzLjUtNjloMjQuMWwxNC44IDI0LjNMMzEzLjIgMGgyNC4xdjY5aC0yM1YzNC44bC0xNi4xIDI0LjgtMTYuMS0yNC44VjY5aC0yMi42bTg5LjItNjloMjN2NDYuMmgzMi42VjY5aC01NS42Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI2U0NGQyNiIgZD0iTTEwNy42IDQ3MWwtMzMtMzcwLjRoMzYyLjhsLTMzIDM3MC4yTDI1NS43IDUxMiIvPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNmMTY1MjkiIGQ9Ik0yNTYgNDgwLjVWMTMxaDE0OC4zTDM3NiA0NDciLz4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNlYmViZWIiIGQ9Ik0xNDIgMTc2LjNoMTE0djQ1LjRoLTY0LjJsNC4yIDQ2LjVoNjB2NDUuM0gxNTQuNG0yIDIyLjhIMjAybDMuMiAzNi4zIDUwLjggMTMuNnY0Ny40bC05My4yLTI2Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIiBmaWxsPSIjZmZmIiBkPSJNMzY5LjYgMTc2LjNIMjU1Ljh2NDUuNGgxMDkuNm0tNC4xIDQ2LjVIMjU1Ljh2NDUuNGg1NmwtNS4zIDU5LTUwLjcgMTMuNnY0Ny4ybDkzLTI1LjgiLz4KPC9zdmc+Cg==);
  --jp-icon-image: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1icmFuZDQganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNGRkYiIGQ9Ik0yLjIgMi4yaDE3LjV2MTcuNUgyLjJ6Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzNGNTFCNSIgZD0iTTIuMiAyLjJ2MTcuNWgxNy41bC4xLTE3LjVIMi4yem0xMi4xIDIuMmMxLjIgMCAyLjIgMSAyLjIgMi4ycy0xIDIuMi0yLjIgMi4yLTIuMi0xLTIuMi0yLjIgMS0yLjIgMi4yLTIuMnpNNC40IDE3LjZsMy4zLTguOCAzLjMgNi42IDIuMi0zLjIgNC40IDUuNEg0LjR6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-info: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUwLjk3OCA1MC45NzgiPgoJPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KCQk8cGF0aCBkPSJNNDMuNTIsNy40NThDMzguNzExLDIuNjQ4LDMyLjMwNywwLDI1LjQ4OSwwQzE4LjY3LDAsMTIuMjY2LDIuNjQ4LDcuNDU4LDcuNDU4CgkJCWMtOS45NDMsOS45NDEtOS45NDMsMjYuMTE5LDAsMzYuMDYyYzQuODA5LDQuODA5LDExLjIxMiw3LjQ1NiwxOC4wMzEsNy40NThjMCwwLDAuMDAxLDAsMC4wMDIsMAoJCQljNi44MTYsMCwxMy4yMjEtMi42NDgsMTguMDI5LTcuNDU4YzQuODA5LTQuODA5LDcuNDU3LTExLjIxMiw3LjQ1Ny0xOC4wM0M1MC45NzcsMTguNjcsNDguMzI4LDEyLjI2Niw0My41Miw3LjQ1OHoKCQkJIE00Mi4xMDYsNDIuMTA1Yy00LjQzMiw0LjQzMS0xMC4zMzIsNi44NzItMTYuNjE1LDYuODcyaC0wLjAwMmMtNi4yODUtMC4wMDEtMTIuMTg3LTIuNDQxLTE2LjYxNy02Ljg3MgoJCQljLTkuMTYyLTkuMTYzLTkuMTYyLTI0LjA3MSwwLTMzLjIzM0MxMy4zMDMsNC40NCwxOS4yMDQsMiwyNS40ODksMmM2LjI4NCwwLDEyLjE4NiwyLjQ0LDE2LjYxNyw2Ljg3MgoJCQljNC40MzEsNC40MzEsNi44NzEsMTAuMzMyLDYuODcxLDE2LjYxN0M0OC45NzcsMzEuNzcyLDQ2LjUzNiwzNy42NzUsNDIuMTA2LDQyLjEwNXoiLz4KCQk8cGF0aCBkPSJNMjMuNTc4LDMyLjIxOGMtMC4wMjMtMS43MzQsMC4xNDMtMy4wNTksMC40OTYtMy45NzJjMC4zNTMtMC45MTMsMS4xMS0xLjk5NywyLjI3Mi0zLjI1MwoJCQljMC40NjgtMC41MzYsMC45MjMtMS4wNjIsMS4zNjctMS41NzVjMC42MjYtMC43NTMsMS4xMDQtMS40NzgsMS40MzYtMi4xNzVjMC4zMzEtMC43MDcsMC40OTUtMS41NDEsMC40OTUtMi41CgkJCWMwLTEuMDk2LTAuMjYtMi4wODgtMC43NzktMi45NzljLTAuNTY1LTAuODc5LTEuNTAxLTEuMzM2LTIuODA2LTEuMzY5Yy0xLjgwMiwwLjA1Ny0yLjk4NSwwLjY2Ny0zLjU1LDEuODMyCgkJCWMtMC4zMDEsMC41MzUtMC41MDMsMS4xNDEtMC42MDcsMS44MTRjLTAuMTM5LDAuNzA3LTAuMjA3LDEuNDMyLTAuMjA3LDIuMTc0aC0yLjkzN2MtMC4wOTEtMi4yMDgsMC40MDctNC4xMTQsMS40OTMtNS43MTkKCQkJYzEuMDYyLTEuNjQsMi44NTUtMi40ODEsNS4zNzgtMi41MjdjMi4xNiwwLjAyMywzLjg3NCwwLjYwOCw1LjE0MSwxLjc1OGMxLjI3OCwxLjE2LDEuOTI5LDIuNzY0LDEuOTUsNC44MTEKCQkJYzAsMS4xNDItMC4xMzcsMi4xMTEtMC40MSwyLjkxMWMtMC4zMDksMC44NDUtMC43MzEsMS41OTMtMS4yNjgsMi4yNDNjLTAuNDkyLDAuNjUtMS4wNjgsMS4zMTgtMS43MywyLjAwMgoJCQljLTAuNjUsMC42OTctMS4zMTMsMS40NzktMS45ODcsMi4zNDZjLTAuMjM5LDAuMzc3LTAuNDI5LDAuNzc3LTAuNTY1LDEuMTk5Yy0wLjE2LDAuOTU5LTAuMjE3LDEuOTUxLTAuMTcxLDIuOTc5CgkJCUMyNi41ODksMzIuMjE4LDIzLjU3OCwzMi4yMTgsMjMuNTc4LDMyLjIxOHogTTIzLjU3OCwzOC4yMnYtMy40ODRoMy4wNzZ2My40ODRIMjMuNTc4eiIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-inspector: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaW5zcGVjdG9yLWljb24tY29sb3IganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY2YzAtMS4xLS45LTItMi0yem0tNSAxNEg0di00aDExdjR6bTAtNUg0VjloMTF2NHptNSA1aC00VjloNHY5eiIvPgo8L3N2Zz4K);
  --jp-icon-json: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtanNvbi1pY29uLWNvbG9yIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI0Y5QTgyNSI+CiAgICA8cGF0aCBkPSJNMjAuMiAxMS44Yy0xLjYgMC0xLjcuNS0xLjcgMSAwIC40LjEuOS4xIDEuMy4xLjUuMS45LjEgMS4zIDAgMS43LTEuNCAyLjMtMy41IDIuM2gtLjl2LTEuOWguNWMxLjEgMCAxLjQgMCAxLjQtLjggMC0uMyAwLS42LS4xLTEgMC0uNC0uMS0uOC0uMS0xLjIgMC0xLjMgMC0xLjggMS4zLTItMS4zLS4yLTEuMy0uNy0xLjMtMiAwLS40LjEtLjguMS0xLjIuMS0uNC4xLS43LjEtMSAwLS44LS40LS43LTEuNC0uOGgtLjVWNC4xaC45YzIuMiAwIDMuNS43IDMuNSAyLjMgMCAuNC0uMS45LS4xIDEuMy0uMS41LS4xLjktLjEgMS4zIDAgLjUuMiAxIDEuNyAxdjEuOHpNMS44IDEwLjFjMS42IDAgMS43LS41IDEuNy0xIDAtLjQtLjEtLjktLjEtMS4zLS4xLS41LS4xLS45LS4xLTEuMyAwLTEuNiAxLjQtMi4zIDMuNS0yLjNoLjl2MS45aC0uNWMtMSAwLTEuNCAwLTEuNC44IDAgLjMgMCAuNi4xIDEgMCAuMi4xLjYuMSAxIDAgMS4zIDAgMS44LTEuMyAyQzYgMTEuMiA2IDExLjcgNiAxM2MwIC40LS4xLjgtLjEgMS4yLS4xLjMtLjEuNy0uMSAxIDAgLjguMy44IDEuNC44aC41djEuOWgtLjljLTIuMSAwLTMuNS0uNi0zLjUtMi4zIDAtLjQuMS0uOS4xLTEuMy4xLS41LjEtLjkuMS0xLjMgMC0uNS0uMi0xLTEuNy0xdi0xLjl6Ii8+CiAgICA8Y2lyY2xlIGN4PSIxMSIgY3k9IjEzLjgiIHI9IjIuMSIvPgogICAgPGNpcmNsZSBjeD0iMTEiIGN5PSI4LjIiIHI9IjIuMSIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-julia: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDMyNSAzMDAiPgogIDxnIGNsYXNzPSJqcC1icmFuZDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjY2IzYzMzIj4KICAgIDxwYXRoIGQ9Ik0gMTUwLjg5ODQzOCAyMjUgQyAxNTAuODk4NDM4IDI2Ni40MjE4NzUgMTE3LjMyMDMxMiAzMDAgNzUuODk4NDM4IDMwMCBDIDM0LjQ3NjU2MiAzMDAgMC44OTg0MzggMjY2LjQyMTg3NSAwLjg5ODQzOCAyMjUgQyAwLjg5ODQzOCAxODMuNTc4MTI1IDM0LjQ3NjU2MiAxNTAgNzUuODk4NDM4IDE1MCBDIDExNy4zMjAzMTIgMTUwIDE1MC44OTg0MzggMTgzLjU3ODEyNSAxNTAuODk4NDM4IDIyNSIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzM4OTgyNiI+CiAgICA8cGF0aCBkPSJNIDIzNy41IDc1IEMgMjM3LjUgMTE2LjQyMTg3NSAyMDMuOTIxODc1IDE1MCAxNjIuNSAxNTAgQyAxMjEuMDc4MTI1IDE1MCA4Ny41IDExNi40MjE4NzUgODcuNSA3NSBDIDg3LjUgMzMuNTc4MTI1IDEyMS4wNzgxMjUgMCAxNjIuNSAwIEMgMjAzLjkyMTg3NSAwIDIzNy41IDMzLjU3ODEyNSAyMzcuNSA3NSIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzk1NThiMiI+CiAgICA8cGF0aCBkPSJNIDMyNC4xMDE1NjIgMjI1IEMgMzI0LjEwMTU2MiAyNjYuNDIxODc1IDI5MC41MjM0MzggMzAwIDI0OS4xMDE1NjIgMzAwIEMgMjA3LjY3OTY4OCAzMDAgMTc0LjEwMTU2MiAyNjYuNDIxODc1IDE3NC4xMDE1NjIgMjI1IEMgMTc0LjEwMTU2MiAxODMuNTc4MTI1IDIwNy42Nzk2ODggMTUwIDI0OS4xMDE1NjIgMTUwIEMgMjkwLjUyMzQzOCAxNTAgMzI0LjEwMTU2MiAxODMuNTc4MTI1IDMyNC4xMDE1NjIgMjI1Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-jupyter-favicon: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTUyIiBoZWlnaHQ9IjE2NSIgdmlld0JveD0iMCAwIDE1MiAxNjUiIHZlcnNpb249IjEuMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgPGcgY2xhc3M9ImpwLWp1cHl0ZXItaWNvbi1jb2xvciIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA3ODk0NywgMTEwLjU4MjkyNykiIGQ9Ik03NS45NDIyODQyLDI5LjU4MDQ1NjEgQzQzLjMwMjM5NDcsMjkuNTgwNDU2MSAxNC43OTY3ODMyLDE3LjY1MzQ2MzQgMCwwIEM1LjUxMDgzMjExLDE1Ljg0MDY4MjkgMTUuNzgxNTM4OSwyOS41NjY3NzMyIDI5LjM5MDQ5NDcsMzkuMjc4NDE3MSBDNDIuOTk5Nyw0OC45ODk4NTM3IDU5LjI3MzcsNTQuMjA2NzgwNSA3NS45NjA1Nzg5LDU0LjIwNjc4MDUgQzkyLjY0NzQ1NzksNTQuMjA2NzgwNSAxMDguOTIxNDU4LDQ4Ljk4OTg1MzcgMTIyLjUzMDY2MywzOS4yNzg0MTcxIEMxMzYuMTM5NDUzLDI5LjU2Njc3MzIgMTQ2LjQxMDI4NCwxNS44NDA2ODI5IDE1MS45MjExNTgsMCBDMTM3LjA4Nzg2OCwxNy42NTM0NjM0IDEwOC41ODI1ODksMjkuNTgwNDU2MSA3NS45NDIyODQyLDI5LjU4MDQ1NjEgTDc1Ljk0MjI4NDIsMjkuNTgwNDU2MSBaIiAvPgogICAgPHBhdGggdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMzczNjgsIDAuNzA0ODc4KSIgZD0iTTc1Ljk3ODQ1NzksMjQuNjI2NDA3MyBDMTA4LjYxODc2MywyNC42MjY0MDczIDEzNy4xMjQ0NTgsMzYuNTUzNDQxNSAxNTEuOTIxMTU4LDU0LjIwNjc4MDUgQzE0Ni40MTAyODQsMzguMzY2MjIyIDEzNi4xMzk0NTMsMjQuNjQwMTMxNyAxMjIuNTMwNjYzLDE0LjkyODQ4NzggQzEwOC45MjE0NTgsNS4yMTY4NDM5IDkyLjY0NzQ1NzksMCA3NS45NjA1Nzg5LDAgQzU5LjI3MzcsMCA0Mi45OTk3LDUuMjE2ODQzOSAyOS4zOTA0OTQ3LDE0LjkyODQ4NzggQzE1Ljc4MTUzODksMjQuNjQwMTMxNyA1LjUxMDgzMjExLDM4LjM2NjIyMiAwLDU0LjIwNjc4MDUgQzE0LjgzMzA4MTYsMzYuNTg5OTI5MyA0My4zMzg1Njg0LDI0LjYyNjQwNzMgNzUuOTc4NDU3OSwyNC42MjY0MDczIEw3NS45Nzg0NTc5LDI0LjYyNjQwNzMgWiIgLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-jupyter: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMzkiIGhlaWdodD0iNTEiIHZpZXdCb3g9IjAgMCAzOSA1MSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgtMTYzOCAtMjI4MSkiPgogICAgIDxnIGNsYXNzPSJqcC1qdXB5dGVyLWljb24tY29sb3IiIGZpbGw9IiNGMzc3MjYiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5Ljc0IDIzMTEuOTgpIiBkPSJNIDE4LjI2NDYgNy4xMzQxMUMgMTAuNDE0NSA3LjEzNDExIDMuNTU4NzIgNC4yNTc2IDAgMEMgMS4zMjUzOSAzLjgyMDQgMy43OTU1NiA3LjEzMDgxIDcuMDY4NiA5LjQ3MzAzQyAxMC4zNDE3IDExLjgxNTIgMTQuMjU1NyAxMy4wNzM0IDE4LjI2OSAxMy4wNzM0QyAyMi4yODIzIDEzLjA3MzQgMjYuMTk2MyAxMS44MTUyIDI5LjQ2OTQgOS40NzMwM0MgMzIuNzQyNCA3LjEzMDgxIDM1LjIxMjYgMy44MjA0IDM2LjUzOCAwQyAzMi45NzA1IDQuMjU3NiAyNi4xMTQ4IDcuMTM0MTEgMTguMjY0NiA3LjEzNDExWiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5LjczIDIyODUuNDgpIiBkPSJNIDE4LjI3MzMgNS45MzkzMUMgMjYuMTIzNSA1LjkzOTMxIDMyLjk3OTMgOC44MTU4MyAzNi41MzggMTMuMDczNEMgMzUuMjEyNiA5LjI1MzAzIDMyLjc0MjQgNS45NDI2MiAyOS40Njk0IDMuNjAwNEMgMjYuMTk2MyAxLjI1ODE4IDIyLjI4MjMgMCAxOC4yNjkgMEMgMTQuMjU1NyAwIDEwLjM0MTcgMS4yNTgxOCA3LjA2ODYgMy42MDA0QyAzLjc5NTU2IDUuOTQyNjIgMS4zMjUzOSA5LjI1MzAzIDAgMTMuMDczNEMgMy41Njc0NSA4LjgyNDYzIDEwLjQyMzIgNS45MzkzMSAxOC4yNzMzIDUuOTM5MzFaIi8+CiAgICA8L2c+CiAgICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjY5LjMgMjI4MS4zMSkiIGQ9Ik0gNS44OTM1MyAyLjg0NEMgNS45MTg4OSAzLjQzMTY1IDUuNzcwODUgNC4wMTM2NyA1LjQ2ODE1IDQuNTE2NDVDIDUuMTY1NDUgNS4wMTkyMiA0LjcyMTY4IDUuNDIwMTUgNC4xOTI5OSA1LjY2ODUxQyAzLjY2NDMgNS45MTY4OCAzLjA3NDQ0IDYuMDAxNTEgMi40OTgwNSA1LjkxMTcxQyAxLjkyMTY2IDUuODIxOSAxLjM4NDYzIDUuNTYxNyAwLjk1NDg5OCA1LjE2NDAxQyAwLjUyNTE3IDQuNzY2MzMgMC4yMjIwNTYgNC4yNDkwMyAwLjA4MzkwMzcgMy42Nzc1N0MgLTAuMDU0MjQ4MyAzLjEwNjExIC0wLjAyMTIzIDIuNTA2MTcgMC4xNzg3ODEgMS45NTM2NEMgMC4zNzg3OTMgMS40MDExIDAuNzM2ODA5IDAuOTIwODE3IDEuMjA3NTQgMC41NzM1MzhDIDEuNjc4MjYgMC4yMjYyNTkgMi4yNDA1NSAwLjAyNzU5MTkgMi44MjMyNiAwLjAwMjY3MjI5QyAzLjYwMzg5IC0wLjAzMDcxMTUgNC4zNjU3MyAwLjI0OTc4OSA0Ljk0MTQyIDAuNzgyNTUxQyA1LjUxNzExIDEuMzE1MzEgNS44NTk1NiAyLjA1Njc2IDUuODkzNTMgMi44NDRaIi8+CiAgICAgIDxwYXRoIHRyYW5zZm9ybT0idHJhbnNsYXRlKDE2MzkuOCAyMzIzLjgxKSIgZD0iTSA3LjQyNzg5IDMuNTgzMzhDIDcuNDYwMDggNC4zMjQzIDcuMjczNTUgNS4wNTgxOSA2Ljg5MTkzIDUuNjkyMTNDIDYuNTEwMzEgNi4zMjYwNyA1Ljk1MDc1IDYuODMxNTYgNS4yODQxMSA3LjE0NDZDIDQuNjE3NDcgNy40NTc2MyAzLjg3MzcxIDcuNTY0MTQgMy4xNDcwMiA3LjQ1MDYzQyAyLjQyMDMyIDcuMzM3MTIgMS43NDMzNiA3LjAwODcgMS4yMDE4NCA2LjUwNjk1QyAwLjY2MDMyOCA2LjAwNTIgMC4yNzg2MSA1LjM1MjY4IDAuMTA1MDE3IDQuNjMyMDJDIC0wLjA2ODU3NTcgMy45MTEzNSAtMC4wMjYyMzYxIDMuMTU0OTQgMC4yMjY2NzUgMi40NTg1NkMgMC40Nzk1ODcgMS43NjIxNyAwLjkzMTY5NyAxLjE1NzEzIDEuNTI1NzYgMC43MjAwMzNDIDIuMTE5ODMgMC4yODI5MzUgMi44MjkxNCAwLjAzMzQzOTUgMy41NjM4OSAwLjAwMzEzMzQ0QyA0LjU0NjY3IC0wLjAzNzQwMzMgNS41MDUyOSAwLjMxNjcwNiA2LjIyOTYxIDAuOTg3ODM1QyA2Ljk1MzkzIDEuNjU4OTYgNy4zODQ4NCAyLjU5MjM1IDcuNDI3ODkgMy41ODMzOEwgNy40Mjc4OSAzLjU4MzM4WiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM4LjM2IDIyODYuMDYpIiBkPSJNIDIuMjc0NzEgNC4zOTYyOUMgMS44NDM2MyA0LjQxNTA4IDEuNDE2NzEgNC4zMDQ0NSAxLjA0Nzk5IDQuMDc4NDNDIDAuNjc5MjY4IDMuODUyNCAwLjM4NTMyOCAzLjUyMTE0IDAuMjAzMzcxIDMuMTI2NTZDIDAuMDIxNDEzNiAyLjczMTk4IC0wLjA0MDM3OTggMi4yOTE4MyAwLjAyNTgxMTYgMS44NjE4MUMgMC4wOTIwMDMxIDEuNDMxOCAwLjI4MzIwNCAxLjAzMTI2IDAuNTc1MjEzIDAuNzEwODgzQyAwLjg2NzIyMiAwLjM5MDUxIDEuMjQ2OTEgMC4xNjQ3MDggMS42NjYyMiAwLjA2MjA1OTJDIDIuMDg1NTMgLTAuMDQwNTg5NyAyLjUyNTYxIC0wLjAxNTQ3MTQgMi45MzA3NiAwLjEzNDIzNUMgMy4zMzU5MSAwLjI4Mzk0MSAzLjY4NzkyIDAuNTUxNTA1IDMuOTQyMjIgMC45MDMwNkMgNC4xOTY1MiAxLjI1NDYyIDQuMzQxNjkgMS42NzQzNiA0LjM1OTM1IDIuMTA5MTZDIDQuMzgyOTkgMi42OTEwNyA0LjE3Njc4IDMuMjU4NjkgMy43ODU5NyAzLjY4NzQ2QyAzLjM5NTE2IDQuMTE2MjQgMi44NTE2NiA0LjM3MTE2IDIuMjc0NzEgNC4zOTYyOUwgMi4yNzQ3MSA0LjM5NjI5WiIvPgogICAgPC9nPgogIDwvZz4+Cjwvc3ZnPgo=);
  --jp-icon-jupyterlab-wordmark: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyMDAiIHZpZXdCb3g9IjAgMCAxODYwLjggNDc1Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0RTRFNEUiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDQ4MC4xMzY0MDEsIDY0LjI3MTQ5MykiPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMDAwMDAsIDU4Ljg3NTU2NikiPgogICAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA4NzYwMywgMC4xNDAyOTQpIj4KICAgICAgICA8cGF0aCBkPSJNLTQyNi45LDE2OS44YzAsNDguNy0zLjcsNjQuNy0xMy42LDc2LjRjLTEwLjgsMTAtMjUsMTUuNS0zOS43LDE1LjVsMy43LDI5IGMyMi44LDAuMyw0NC44LTcuOSw2MS45LTIzLjFjMTcuOC0xOC41LDI0LTQ0LjEsMjQtODMuM1YwSC00Mjd2MTcwLjFMLTQyNi45LDE2OS44TC00MjYuOSwxNjkuOHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTU1LjA0NTI5NiwgNTYuODM3MTA0KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuNTYyNDUzLCAxLjc5OTg0MikiPgogICAgICAgIDxwYXRoIGQ9Ik0tMzEyLDE0OGMwLDIxLDAsMzkuNSwxLjcsNTUuNGgtMzEuOGwtMi4xLTMzLjNoLTAuOGMtNi43LDExLjYtMTYuNCwyMS4zLTI4LDI3LjkgYy0xMS42LDYuNi0yNC44LDEwLTM4LjIsOS44Yy0zMS40LDAtNjktMTcuNy02OS04OVYwaDM2LjR2MTEyLjdjMCwzOC43LDExLjYsNjQuNyw0NC42LDY0LjdjMTAuMy0wLjIsMjAuNC0zLjUsMjguOS05LjQgYzguNS01LjksMTUuMS0xNC4zLDE4LjktMjMuOWMyLjItNi4xLDMuMy0xMi41LDMuMy0xOC45VjAuMmgzNi40VjE0OEgtMzEyTC0zMTIsMTQ4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzOTAuMDEzMzIyLCA1My40Nzk2MzgpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS43MDY0NTgsIDAuMjMxNDI1KSI+CiAgICAgICAgPHBhdGggZD0iTS00NzguNiw3MS40YzAtMjYtMC44LTQ3LTEuNy02Ni43aDMyLjdsMS43LDM0LjhoMC44YzcuMS0xMi41LDE3LjUtMjIuOCwzMC4xLTI5LjcgYzEyLjUtNywyNi43LTEwLjMsNDEtOS44YzQ4LjMsMCw4NC43LDQxLjcsODQuNywxMDMuM2MwLDczLjEtNDMuNywxMDkuMi05MSwxMDkuMmMtMTIuMSwwLjUtMjQuMi0yLjItMzUtNy44IGMtMTAuOC01LjYtMTkuOS0xMy45LTI2LjYtMjQuMmgtMC44VjI5MWgtMzZ2LTIyMEwtNDc4LjYsNzEuNEwtNDc4LjYsNzEuNHogTS00NDIuNiwxMjUuNmMwLjEsNS4xLDAuNiwxMC4xLDEuNywxNS4xIGMzLDEyLjMsOS45LDIzLjMsMTkuOCwzMS4xYzkuOSw3LjgsMjIuMSwxMi4xLDM0LjcsMTIuMWMzOC41LDAsNjAuNy0zMS45LDYwLjctNzguNWMwLTQwLjctMjEuMS03NS42LTU5LjUtNzUuNiBjLTEyLjksMC40LTI1LjMsNS4xLTM1LjMsMTMuNGMtOS45LDguMy0xNi45LDE5LjctMTkuNiwzMi40Yy0xLjUsNC45LTIuMywxMC0yLjUsMTUuMVYxMjUuNkwtNDQyLjYsMTI1LjZMLTQ0Mi42LDEyNS42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSg2MDYuNzQwNzI2LCA1Ni44MzcxMDQpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC43NTEyMjYsIDEuOTg5Mjk5KSI+CiAgICAgICAgPHBhdGggZD0iTS00NDAuOCwwbDQzLjcsMTIwLjFjNC41LDEzLjQsOS41LDI5LjQsMTIuOCw0MS43aDAuOGMzLjctMTIuMiw3LjktMjcuNywxMi44LTQyLjQgbDM5LjctMTE5LjJoMzguNUwtMzQ2LjksMTQ1Yy0yNiw2OS43LTQzLjcsMTA1LjQtNjguNiwxMjcuMmMtMTIuNSwxMS43LTI3LjksMjAtNDQuNiwyMy45bC05LjEtMzEuMSBjMTEuNy0zLjksMjIuNS0xMC4xLDMxLjgtMTguMWMxMy4yLTExLjEsMjMuNy0yNS4yLDMwLjYtNDEuMmMxLjUtMi44LDIuNS01LjcsMi45LTguOGMtMC4zLTMuMy0xLjItNi42LTIuNS05LjdMLTQ4MC4yLDAuMSBoMzkuN0wtNDQwLjgsMEwtNDQwLjgsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoODIyLjc0ODEwNCwgMC4wMDAwMDApIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS40NjQwNTAsIDAuMzc4OTE0KSI+CiAgICAgICAgPHBhdGggZD0iTS00MTMuNywwdjU4LjNoNTJ2MjguMmgtNTJWMTk2YzAsMjUsNywzOS41LDI3LjMsMzkuNWM3LjEsMC4xLDE0LjItMC43LDIxLjEtMi41IGwxLjcsMjcuN2MtMTAuMywzLjctMjEuMyw1LjQtMzIuMiw1Yy03LjMsMC40LTE0LjYtMC43LTIxLjMtMy40Yy02LjgtMi43LTEyLjktNi44LTE3LjktMTIuMWMtMTAuMy0xMC45LTE0LjEtMjktMTQuMS01Mi45IFY4Ni41aC0zMVY1OC4zaDMxVjkuNkwtNDEzLjcsMEwtNDEzLjcsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOTc0LjQzMzI4NiwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuOTkwMDM0LCAwLjYxMDMzOSkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDQ1LjgsMTEzYzAuOCw1MCwzMi4yLDcwLjYsNjguNiw3MC42YzE5LDAuNiwzNy45LTMsNTUuMy0xMC41bDYuMiwyNi40IGMtMjAuOSw4LjktNDMuNSwxMy4xLTY2LjIsMTIuNmMtNjEuNSwwLTk4LjMtNDEuMi05OC4zLTEwMi41Qy00ODAuMiw0OC4yLTQ0NC43LDAtMzg2LjUsMGM2NS4yLDAsODIuNyw1OC4zLDgyLjcsOTUuNyBjLTAuMSw1LjgtMC41LDExLjUtMS4yLDE3LjJoLTE0MC42SC00NDUuOEwtNDQ1LjgsMTEzeiBNLTMzOS4yLDg2LjZjMC40LTIzLjUtOS41LTYwLjEtNTAuNC02MC4xIGMtMzYuOCwwLTUyLjgsMzQuNC01NS43LDYwLjFILTMzOS4yTC0zMzkuMiw4Ni42TC0zMzkuMiw4Ni42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxMjAxLjk2MTA1OCwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuMTc5NjQwLCAwLjcwNTA2OCkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDc4LjYsNjhjMC0yMy45LTAuNC00NC41LTEuNy02My40aDMxLjhsMS4yLDM5LjloMS43YzkuMS0yNy4zLDMxLTQ0LjUsNTUuMy00NC41IGMzLjUtMC4xLDcsMC40LDEwLjMsMS4ydjM0LjhjLTQuMS0wLjktOC4yLTEuMy0xMi40LTEuMmMtMjUuNiwwLTQzLjcsMTkuNy00OC43LDQ3LjRjLTEsNS43LTEuNiwxMS41LTEuNywxNy4ydjEwOC4zaC0zNlY2OCBMLTQ3OC42LDY4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCBkPSJNMTM1Mi4zLDMyNi4yaDM3VjI4aC0zN1YzMjYuMnogTTE2MDQuOCwzMjYuMmMtMi41LTEzLjktMy40LTMxLjEtMy40LTQ4Ljd2LTc2IGMwLTQwLjctMTUuMS04My4xLTc3LjMtODMuMWMtMjUuNiwwLTUwLDcuMS02Ni44LDE4LjFsOC40LDI0LjRjMTQuMy05LjIsMzQtMTUuMSw1My0xNS4xYzQxLjYsMCw0Ni4yLDMwLjIsNDYuMiw0N3Y0LjIgYy03OC42LTAuNC0xMjIuMywyNi41LTEyMi4zLDc1LjZjMCwyOS40LDIxLDU4LjQsNjIuMiw1OC40YzI5LDAsNTAuOS0xNC4zLDYyLjItMzAuMmgxLjNsMi45LDI1LjZIMTYwNC44eiBNMTU2NS43LDI1Ny43IGMwLDMuOC0wLjgsOC0yLjEsMTEuOGMtNS45LDE3LjItMjIuNywzNC00OS4yLDM0Yy0xOC45LDAtMzQuOS0xMS4zLTM0LjktMzUuM2MwLTM5LjUsNDUuOC00Ni42LDg2LjItNDUuOFYyNTcuN3ogTTE2OTguNSwzMjYuMiBsMS43LTMzLjZoMS4zYzE1LjEsMjYuOSwzOC43LDM4LjIsNjguMSwzOC4yYzQ1LjQsMCw5MS4yLTM2LjEsOTEuMi0xMDguOGMwLjQtNjEuNy0zNS4zLTEwMy43LTg1LjctMTAzLjcgYy0zMi44LDAtNTYuMywxNC43LTY5LjMsMzcuNGgtMC44VjI4aC0zNi42djI0NS43YzAsMTguMS0wLjgsMzguNi0xLjcsNTIuNUgxNjk4LjV6IE0xNzA0LjgsMjA4LjJjMC01LjksMS4zLTEwLjksMi4xLTE1LjEgYzcuNi0yOC4xLDMxLjEtNDUuNCw1Ni4zLTQ1LjRjMzkuNSwwLDYwLjUsMzQuOSw2MC41LDc1LjZjMCw0Ni42LTIzLjEsNzguMS02MS44LDc4LjFjLTI2LjksMC00OC4zLTE3LjYtNTUuNS00My4zIGMtMC44LTQuMi0xLjctOC44LTEuNy0xMy40VjIwOC4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgZmlsbD0iIzYxNjE2MSIgZD0iTTE1IDlIOXY2aDZWOXptLTIgNGgtMnYtMmgydjJ6bTgtMlY5aC0yVjdjMC0xLjEtLjktMi0yLTJoLTJWM2gtMnYyaC0yVjNIOXYySDdjLTEuMSAwLTIgLjktMiAydjJIM3YyaDJ2MkgzdjJoMnYyYzAgMS4xLjkgMiAyIDJoMnYyaDJ2LTJoMnYyaDJ2LTJoMmMxLjEgMCAyLS45IDItMnYtMmgydi0yaC0ydi0yaDJ6bS00IDZIN1Y3aDEwdjEweiIvPgo8L3N2Zz4K);
  --jp-icon-keyboard: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMTdjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY3YzAtMS4xLS45LTItMi0yem0tOSAzaDJ2MmgtMlY4em0wIDNoMnYyaC0ydi0yek04IDhoMnYySDhWOHptMCAzaDJ2Mkg4di0yem0tMSAySDV2LTJoMnYyem0wLTNINVY4aDJ2MnptOSA3SDh2LTJoOHYyem0wLTRoLTJ2LTJoMnYyem0wLTNoLTJWOGgydjJ6bTMgM2gtMnYtMmgydjJ6bTAtM2gtMlY4aDJ2MnoiLz4KPC9zdmc+Cg==);
  --jp-icon-launch: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMzIgMzIiIHdpZHRoPSIzMiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0yNiwyOEg2YTIuMDAyNywyLjAwMjcsMCwwLDEtMi0yVjZBMi4wMDI3LDIuMDAyNywwLDAsMSw2LDRIMTZWNkg2VjI2SDI2VjE2aDJWMjZBMi4wMDI3LDIuMDAyNywwLDAsMSwyNiwyOFoiLz4KICAgIDxwb2x5Z29uIHBvaW50cz0iMjAgMiAyMCA0IDI2LjU4NiA0IDE4IDEyLjU4NiAxOS40MTQgMTQgMjggNS40MTQgMjggMTIgMzAgMTIgMzAgMiAyMCAyIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-launcher: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkgMTlINVY1aDdWM0g1YTIgMiAwIDAwLTIgMnYxNGEyIDIgMCAwMDIgMmgxNGMxLjEgMCAyLS45IDItMnYtN2gtMnY3ek0xNCAzdjJoMy41OWwtOS44MyA5LjgzIDEuNDEgMS40MUwxOSA2LjQxVjEwaDJWM2gtN3oiLz4KPC9zdmc+Cg==);
  --jp-icon-line-form: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGZpbGw9IndoaXRlIiBkPSJNNS44OCA0LjEyTDEzLjc2IDEybC03Ljg4IDcuODhMOCAyMmwxMC0xMEw4IDJ6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-link: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMuOSAxMmMwLTEuNzEgMS4zOS0zLjEgMy4xLTMuMWg0VjdIN2MtMi43NiAwLTUgMi4yNC01IDVzMi4yNCA1IDUgNWg0di0xLjlIN2MtMS43MSAwLTMuMS0xLjM5LTMuMS0zLjF6TTggMTNoOHYtMkg4djJ6bTktNmgtNHYxLjloNGMxLjcxIDAgMy4xIDEuMzkgMy4xIDMuMXMtMS4zOSAzLjEtMy4xIDMuMWgtNFYxN2g0YzIuNzYgMCA1LTIuMjQgNS01cy0yLjI0LTUtNS01eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xOSA1djE0SDVWNWgxNG0xLjEtMkgzLjljLS41IDAtLjkuNC0uOS45djE2LjJjMCAuNC40LjkuOS45aDE2LjJjLjQgMCAuOS0uNS45LS45VjMuOWMwLS41LS41LS45LS45LS45ek0xMSA3aDZ2MmgtNlY3em0wIDRoNnYyaC02di0yem0wIDRoNnYyaC02ek03IDdoMnYySDd6bTAgNGgydjJIN3ptMCA0aDJ2Mkg3eiIvPgo8L3N2Zz4K);
  --jp-icon-markdown: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjN0IxRkEyIiBkPSJNNSAxNC45aDEybC02LjEgNnptOS40LTYuOGMwLTEuMy0uMS0yLjktLjEtNC41LS40IDEuNC0uOSAyLjktMS4zIDQuM2wtMS4zIDQuM2gtMkw4LjUgNy45Yy0uNC0xLjMtLjctMi45LTEtNC4zLS4xIDEuNi0uMSAzLjItLjIgNC42TDcgMTIuNEg0LjhsLjctMTFoMy4zTDEwIDVjLjQgMS4yLjcgMi43IDEgMy45LjMtMS4yLjctMi42IDEtMy45bDEuMi0zLjdoMy4zbC42IDExaC0yLjRsLS4zLTQuMnoiLz4KPC9zdmc+Cg==);
  --jp-icon-move-down: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBkPSJNMTIuNDcxIDcuNTI4OTlDMTIuNzYzMiA3LjIzNjg0IDEyLjc2MzIgNi43NjMxNiAxMi40NzEgNi40NzEwMVY2LjQ3MTAxQzEyLjE3OSA2LjE3OTA1IDExLjcwNTcgNi4xNzg4NCAxMS40MTM1IDYuNDcwNTRMNy43NSAxMC4xMjc1VjEuNzVDNy43NSAxLjMzNTc5IDcuNDE0MjEgMSA3IDFWMUM2LjU4NTc5IDEgNi4yNSAxLjMzNTc5IDYuMjUgMS43NVYxMC4xMjc1TDIuNTk3MjYgNi40NjgyMkMyLjMwMzM4IDYuMTczODEgMS44MjY0MSA2LjE3MzU5IDEuNTMyMjYgNi40Njc3NFY2LjQ2Nzc0QzEuMjM4MyA2Ljc2MTcgMS4yMzgzIDcuMjM4MyAxLjUzMjI2IDcuNTMyMjZMNi4yOTI4OSAxMi4yOTI5QzYuNjgzNDIgMTIuNjgzNCA3LjMxNjU4IDEyLjY4MzQgNy43MDcxMSAxMi4yOTI5TDEyLjQ3MSA3LjUyODk5WiIgZmlsbD0iIzYxNjE2MSIvPgo8L3N2Zz4K);
  --jp-icon-move-up: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBkPSJNMS41Mjg5OSA2LjQ3MTAxQzEuMjM2ODQgNi43NjMxNiAxLjIzNjg0IDcuMjM2ODQgMS41Mjg5OSA3LjUyODk5VjcuNTI4OTlDMS44MjA5NSA3LjgyMDk1IDIuMjk0MjYgNy44MjExNiAyLjU4NjQ5IDcuNTI5NDZMNi4yNSAzLjg3MjVWMTIuMjVDNi4yNSAxMi42NjQyIDYuNTg1NzkgMTMgNyAxM1YxM0M3LjQxNDIxIDEzIDcuNzUgMTIuNjY0MiA3Ljc1IDEyLjI1VjMuODcyNUwxMS40MDI3IDcuNTMxNzhDMTEuNjk2NiA3LjgyNjE5IDEyLjE3MzYgNy44MjY0MSAxMi40Njc3IDcuNTMyMjZWNy41MzIyNkMxMi43NjE3IDcuMjM4MyAxMi43NjE3IDYuNzYxNyAxMi40Njc3IDYuNDY3NzRMNy43MDcxMSAxLjcwNzExQzcuMzE2NTggMS4zMTY1OCA2LjY4MzQyIDEuMzE2NTggNi4yOTI4OSAxLjcwNzExTDEuNTI4OTkgNi40NzEwMVoiIGZpbGw9IiM2MTYxNjEiLz4KPC9zdmc+Cg==);
  --jp-icon-new-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwIDZoLThsLTItMkg0Yy0xLjExIDAtMS45OS44OS0xLjk5IDJMMiAxOGMwIDEuMTEuODkgMiAyIDJoMTZjMS4xMSAwIDItLjg5IDItMlY4YzAtMS4xMS0uODktMi0yLTJ6bS0xIDhoLTN2M2gtMnYtM2gtM3YtMmgzVjloMnYzaDN2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-not-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI1IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDMgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMTkgMTcuMTg0NCAyLjk2OTY4IDE0LjMwMzIgMS44NjA5NCAxMS40NDA5WiIvPgogICAgPHBhdGggY2xhc3M9ImpwLWljb24yIiBzdHJva2U9IiMzMzMzMzMiIHN0cm9rZS13aWR0aD0iMiIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOS4zMTU5MiA5LjMyMDMxKSIgZD0iTTcuMzY4NDIgMEwwIDcuMzY0NzkiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDkuMzE1OTIgMTYuNjgzNikgc2NhbGUoMSAtMSkiIGQ9Ik03LjM2ODQyIDBMMCA3LjM2NDc5Ii8+Cjwvc3ZnPgo=);
  --jp-icon-notebook: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtbm90ZWJvb2staWNvbi1jb2xvciBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNFRjZDMDAiPgogICAgPHBhdGggZD0iTTE4LjcgMy4zdjE1LjRIMy4zVjMuM2gxNS40bTEuNS0xLjVIMS44djE4LjNoMTguM2wuMS0xOC4zeiIvPgogICAgPHBhdGggZD0iTTE2LjUgMTYuNWwtNS40LTQuMy01LjYgNC4zdi0xMWgxMXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-numbering: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTQgMTlINlYxOS41SDVWMjAuNUg2VjIxSDRWMjJIN1YxOEg0VjE5Wk01IDEwSDZWNkg0VjdINVYxMFpNNCAxM0g1LjhMNCAxNS4xVjE2SDdWMTVINS4yTDcgMTIuOVYxMkg0VjEzWk05IDdWOUgyM1Y3SDlaTTkgMjFIMjNWMTlIOVYyMVpNOSAxNUgyM1YxM0g5VjE1WiIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-offline-bolt: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDIuMDJjLTUuNTEgMC05Ljk4IDQuNDctOS45OCA5Ljk4czQuNDcgOS45OCA5Ljk4IDkuOTggOS45OC00LjQ3IDkuOTgtOS45OFMxNy41MSAyLjAyIDEyIDIuMDJ6TTExLjQ4IDIwdi02LjI2SDhMMTMgNHY2LjI2aDMuMzVMMTEuNDggMjB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-palette: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE4IDEzVjIwSDRWNkg5LjAyQzkuMDcgNS4yOSA5LjI0IDQuNjIgOS41IDRINEMyLjkgNCAyIDQuOSAyIDZWMjBDMiAyMS4xIDIuOSAyMiA0IDIySDE4QzE5LjEgMjIgMjAgMjEuMSAyMCAyMFYxNUwxOCAxM1pNMTkuMyA4Ljg5QzE5Ljc0IDguMTkgMjAgNy4zOCAyMCA2LjVDMjAgNC4wMSAxNy45OSAyIDE1LjUgMkMxMy4wMSAyIDExIDQuMDEgMTEgNi41QzExIDguOTkgMTMuMDEgMTEgMTUuNDkgMTFDMTYuMzcgMTEgMTcuMTkgMTAuNzQgMTcuODggMTAuM0wyMSAxMy40MkwyMi40MiAxMkwxOS4zIDguODlaTTE1LjUgOUMxNC4xMiA5IDEzIDcuODggMTMgNi41QzEzIDUuMTIgMTQuMTIgNCAxNS41IDRDMTYuODggNCAxOCA1LjEyIDE4IDYuNUMxOCA3Ljg4IDE2Ljg4IDkgMTUuNSA5WiIvPgogICAgPHBhdGggZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIGQ9Ik00IDZIOS4wMTg5NEM5LjAwNjM5IDYuMTY1MDIgOSA2LjMzMTc2IDkgNi41QzkgOC44MTU3NyAxMC4yMTEgMTAuODQ4NyAxMi4wMzQzIDEySDlWMTRIMTZWMTIuOTgxMUMxNi41NzAzIDEyLjkzNzcgMTcuMTIgMTIuODIwNyAxNy42Mzk2IDEyLjYzOTZMMTggMTNWMjBINFY2Wk04IDhINlYxMEg4VjhaTTYgMTJIOFYxNEg2VjEyWk04IDE2SDZWMThIOFYxNlpNOSAxNkgxNlYxOEg5VjE2WiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-paste: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE5IDJoLTQuMThDMTQuNC44NCAxMy4zIDAgMTIgMGMtMS4zIDAtMi40Ljg0LTIuODIgMkg1Yy0xLjEgMC0yIC45LTIgMnYxNmMwIDEuMS45IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjRjMC0xLjEtLjktMi0yLTJ6bS03IDBjLjU1IDAgMSAuNDUgMSAxcy0uNDUgMS0xIDEtMS0uNDUtMS0xIC40NS0xIDEtMXptNyAxOEg1VjRoMnYzaDEwVjRoMnYxNnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-pdf: url(data:image/svg+xml;base64,PHN2ZwogICB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyMiAyMiIgd2lkdGg9IjE2Ij4KICAgIDxwYXRoIHRyYW5zZm9ybT0icm90YXRlKDQ1KSIgY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI0ZGMkEyQSIKICAgICAgIGQ9Im0gMjIuMzQ0MzY5LC0zLjAxNjM2NDIgaCA1LjYzODYwNCB2IDEuNTc5MjQzMyBoIC0zLjU0OTIyNyB2IDEuNTA4NjkyOTkgaCAzLjMzNzU3NiBWIDEuNjUwODE1NCBoIC0zLjMzNzU3NiB2IDMuNDM1MjYxMyBoIC0yLjA4OTM3NyB6IG0gLTcuMTM2NDQ0LDEuNTc5MjQzMyB2IDQuOTQzOTU0MyBoIDAuNzQ4OTIgcSAxLjI4MDc2MSwwIDEuOTUzNzAzLC0wLjYzNDk1MzUgMC42NzgzNjksLTAuNjM0OTUzNSAwLjY3ODM2OSwtMS44NDUxNjQxIDAsLTEuMjA0NzgzNTUgLTAuNjcyOTQyLC0xLjgzNDMxMDExIC0wLjY3Mjk0MiwtMC42Mjk1MjY1OSAtMS45NTkxMywtMC42Mjk1MjY1OSB6IG0gLTIuMDg5Mzc3LC0xLjU3OTI0MzMgaCAyLjIwMzM0MyBxIDEuODQ1MTY0LDAgMi43NDYwMzksMC4yNjU5MjA3IDAuOTA2MzAxLDAuMjYwNDkzNyAxLjU1MjEwOCwwLjg5MDAyMDMgMC41Njk4MywwLjU0ODEyMjMgMC44NDY2MDUsMS4yNjQ0ODAwNiAwLjI3Njc3NCwwLjcxNjM1NzgxIDAuMjc2Nzc0LDEuNjIyNjU4OTQgMCwwLjkxNzE1NTEgLTAuMjc2Nzc0LDEuNjM4OTM5OSAtMC4yNzY3NzUsMC43MTYzNTc4IC0wLjg0NjYwNSwxLjI2NDQ4IC0wLjY1MTIzNCwwLjYyOTUyNjYgLTEuNTYyOTYyLDAuODk1NDQ3MyAtMC45MTE3MjgsMC4yNjA0OTM3IC0yLjczNTE4NSwwLjI2MDQ5MzcgaCAtMi4yMDMzNDMgeiBtIC04LjE0NTg1NjUsMCBoIDMuNDY3ODIzIHEgMS41NDY2ODE2LDAgMi4zNzE1Nzg1LDAuNjg5MjIzIDAuODMwMzI0LDAuNjgzNzk2MSAwLjgzMDMyNCwxLjk1MzcwMzE0IDAsMS4yNzUzMzM5NyAtMC44MzAzMjQsMS45NjQ1NTcwNiBRIDkuOTg3MTk2MSwyLjI3NDkxNSA4LjQ0MDUxNDUsMi4yNzQ5MTUgSCA3LjA2MjA2ODQgViA1LjA4NjA3NjcgSCA0Ljk3MjY5MTUgWiBtIDIuMDg5Mzc2OSwxLjUxNDExOTkgdiAyLjI2MzAzOTQzIGggMS4xNTU5NDEgcSAwLjYwNzgxODgsMCAwLjkzODg2MjksLTAuMjkzMDU1NDcgMC4zMzEwNDQxLC0wLjI5ODQ4MjQxIDAuMzMxMDQ0MSwtMC44NDExNzc3MiAwLC0wLjU0MjY5NTMxIC0wLjMzMTA0NDEsLTAuODM1NzUwNzQgLTAuMzMxMDQ0MSwtMC4yOTMwNTU1IC0wLjkzODg2MjksLTAuMjkzMDU1NSB6IgovPgo8L3N2Zz4K);
  --jp-icon-python: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iLTEwIC0xMCAxMzEuMTYxMzYxNjk0MzM1OTQgMTMyLjM4ODk5OTkzODk2NDg0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMzA2OTk4IiBkPSJNIDU0LjkxODc4NSw5LjE5Mjc0MjFlLTQgQyA1MC4zMzUxMzIsMC4wMjIyMTcyNyA0NS45NTc4NDYsMC40MTMxMzY5NyA0Mi4xMDYyODUsMS4wOTQ2NjkzIDMwLjc2MDA2OSwzLjA5OTE3MzEgMjguNzAwMDM2LDcuMjk0NzcxNCAyOC43MDAwMzUsMTUuMDMyMTY5IHYgMTAuMjE4NzUgaCAyNi44MTI1IHYgMy40MDYyNSBoIC0yNi44MTI1IC0xMC4wNjI1IGMgLTcuNzkyNDU5LDAgLTE0LjYxNTc1ODgsNC42ODM3MTcgLTE2Ljc0OTk5OTgsMTMuNTkzNzUgLTIuNDYxODE5OTgsMTAuMjEyOTY2IC0yLjU3MTAxNTA4LDE2LjU4NjAyMyAwLDI3LjI1IDEuOTA1OTI4Myw3LjkzNzg1MiA2LjQ1NzU0MzIsMTMuNTkzNzQ4IDE0LjI0OTk5OTgsMTMuNTkzNzUgaCA5LjIxODc1IHYgLTEyLjI1IGMgMCwtOC44NDk5MDIgNy42NTcxNDQsLTE2LjY1NjI0OCAxNi43NSwtMTYuNjU2MjUgaCAyNi43ODEyNSBjIDcuNDU0OTUxLDAgMTMuNDA2MjUzLC02LjEzODE2NCAxMy40MDYyNSwtMTMuNjI1IHYgLTI1LjUzMTI1IGMgMCwtNy4yNjYzMzg2IC02LjEyOTk4LC0xMi43MjQ3NzcxIC0xMy40MDYyNSwtMTMuOTM3NDk5NyBDIDY0LjI4MTU0OCwwLjMyNzk0Mzk3IDU5LjUwMjQzOCwtMC4wMjAzNzkwMyA1NC45MTg3ODUsOS4xOTI3NDIxZS00IFogbSAtMTQuNSw4LjIxODc1MDEyNTc5IGMgMi43Njk1NDcsMCA1LjAzMTI1LDIuMjk4NjQ1NiA1LjAzMTI1LDUuMTI0OTk5NiAtMmUtNiwyLjgxNjMzNiAtMi4yNjE3MDMsNS4wOTM3NSAtNS4wMzEyNSw1LjA5Mzc1IC0yLjc3OTQ3NiwtMWUtNiAtNS4wMzEyNSwtMi4yNzc0MTUgLTUuMDMxMjUsLTUuMDkzNzUgLTEwZS03LC0yLjgyNjM1MyAyLjI1MTc3NCwtNS4xMjQ5OTk2IDUuMDMxMjUsLTUuMTI0OTk5NiB6Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI2ZmZDQzYiIgZD0ibSA4NS42Mzc1MzUsMjguNjU3MTY5IHYgMTEuOTA2MjUgYyAwLDkuMjMwNzU1IC03LjgyNTg5NSwxNi45OTk5OTkgLTE2Ljc1LDE3IGggLTI2Ljc4MTI1IGMgLTcuMzM1ODMzLDAgLTEzLjQwNjI0OSw2LjI3ODQ4MyAtMTMuNDA2MjUsMTMuNjI1IHYgMjUuNTMxMjQ3IGMgMCw3LjI2NjM0NCA2LjMxODU4OCwxMS41NDAzMjQgMTMuNDA2MjUsMTMuNjI1MDA0IDguNDg3MzMxLDIuNDk1NjEgMTYuNjI2MjM3LDIuOTQ2NjMgMjYuNzgxMjUsMCA2Ljc1MDE1NSwtMS45NTQzOSAxMy40MDYyNTMsLTUuODg3NjEgMTMuNDA2MjUsLTEzLjYyNTAwNCBWIDg2LjUwMDkxOSBoIC0yNi43ODEyNSB2IC0zLjQwNjI1IGggMjYuNzgxMjUgMTMuNDA2MjU0IGMgNy43OTI0NjEsMCAxMC42OTYyNTEsLTUuNDM1NDA4IDEzLjQwNjI0MSwtMTMuNTkzNzUgMi43OTkzMywtOC4zOTg4ODYgMi42ODAyMiwtMTYuNDc1Nzc2IDAsLTI3LjI1IC0xLjkyNTc4LC03Ljc1NzQ0MSAtNS42MDM4NywtMTMuNTkzNzUgLTEzLjQwNjI0MSwtMTMuNTkzNzUgeiBtIC0xNS4wNjI1LDY0LjY1NjI1IGMgMi43Nzk0NzgsM2UtNiA1LjAzMTI1LDIuMjc3NDE3IDUuMDMxMjUsNS4wOTM3NDcgLTJlLTYsMi44MjYzNTQgLTIuMjUxNzc1LDUuMTI1MDA0IC01LjAzMTI1LDUuMTI1MDA0IC0yLjc2OTU1LDAgLTUuMDMxMjUsLTIuMjk4NjUgLTUuMDMxMjUsLTUuMTI1MDA0IDJlLTYsLTIuODE2MzMgMi4yNjE2OTcsLTUuMDkzNzQ3IDUuMDMxMjUsLTUuMDkzNzQ3IHoiLz4KPC9zdmc+Cg==);
  --jp-icon-r-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjE5NkYzIiBkPSJNNC40IDIuNWMxLjItLjEgMi45LS4zIDQuOS0uMyAyLjUgMCA0LjEuNCA1LjIgMS4zIDEgLjcgMS41IDEuOSAxLjUgMy41IDAgMi0xLjQgMy41LTIuOSA0LjEgMS4yLjQgMS43IDEuNiAyLjIgMyAuNiAxLjkgMSAzLjkgMS4zIDQuNmgtMy44Yy0uMy0uNC0uOC0xLjctMS4yLTMuN3MtMS4yLTIuNi0yLjYtMi42aC0uOXY2LjRINC40VjIuNXptMy43IDYuOWgxLjRjMS45IDAgMi45LS45IDIuOS0yLjNzLTEtMi4zLTIuOC0yLjNjLS43IDAtMS4zIDAtMS42LjJ2NC41aC4xdi0uMXoiLz4KPC9zdmc+Cg==);
  --jp-icon-react: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMTUwIDE1MCA1NDEuOSAyOTUuMyI+CiAgPGcgY2xhc3M9ImpwLWljb24tYnJhbmQyIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzYxREFGQiI+CiAgICA8cGF0aCBkPSJNNjY2LjMgMjk2LjVjMC0zMi41LTQwLjctNjMuMy0xMDMuMS04Mi40IDE0LjQtNjMuNiA4LTExNC4yLTIwLjItMTMwLjQtNi41LTMuOC0xNC4xLTUuNi0yMi40LTUuNnYyMi4zYzQuNiAwIDguMy45IDExLjQgMi42IDEzLjYgNy44IDE5LjUgMzcuNSAxNC45IDc1LjctMS4xIDkuNC0yLjkgMTkuMy01LjEgMjkuNC0xOS42LTQuOC00MS04LjUtNjMuNS0xMC45LTEzLjUtMTguNS0yNy41LTM1LjMtNDEuNi01MCAzMi42LTMwLjMgNjMuMi00Ni45IDg0LTQ2LjlWNzhjLTI3LjUgMC02My41IDE5LjYtOTkuOSA1My42LTM2LjQtMzMuOC03Mi40LTUzLjItOTkuOS01My4ydjIyLjNjMjAuNyAwIDUxLjQgMTYuNSA4NCA0Ni42LTE0IDE0LjctMjggMzEuNC00MS4zIDQ5LjktMjIuNiAyLjQtNDQgNi4xLTYzLjYgMTEtMi4zLTEwLTQtMTkuNy01LjItMjktNC43LTM4LjIgMS4xLTY3LjkgMTQuNi03NS44IDMtMS44IDYuOS0yLjYgMTEuNS0yLjZWNzguNWMtOC40IDAtMTYgMS44LTIyLjYgNS42LTI4LjEgMTYuMi0zNC40IDY2LjctMTkuOSAxMzAuMS02Mi4yIDE5LjItMTAyLjcgNDkuOS0xMDIuNyA4Mi4zIDAgMzIuNSA0MC43IDYzLjMgMTAzLjEgODIuNC0xNC40IDYzLjYtOCAxMTQuMiAyMC4yIDEzMC40IDYuNSAzLjggMTQuMSA1LjYgMjIuNSA1LjYgMjcuNSAwIDYzLjUtMTkuNiA5OS45LTUzLjYgMzYuNCAzMy44IDcyLjQgNTMuMiA5OS45IDUzLjIgOC40IDAgMTYtMS44IDIyLjYtNS42IDI4LjEtMTYuMiAzNC40LTY2LjcgMTkuOS0xMzAuMSA2Mi0xOS4xIDEwMi41LTQ5LjkgMTAyLjUtODIuM3ptLTEzMC4yLTY2LjdjLTMuNyAxMi45LTguMyAyNi4yLTEzLjUgMzkuNS00LjEtOC04LjQtMTYtMTMuMS0yNC00LjYtOC05LjUtMTUuOC0xNC40LTIzLjQgMTQuMiAyLjEgMjcuOSA0LjcgNDEgNy45em0tNDUuOCAxMDYuNWMtNy44IDEzLjUtMTUuOCAyNi4zLTI0LjEgMzguMi0xNC45IDEuMy0zMCAyLTQ1LjIgMi0xNS4xIDAtMzAuMi0uNy00NS0xLjktOC4zLTExLjktMTYuNC0yNC42LTI0LjItMzgtNy42LTEzLjEtMTQuNS0yNi40LTIwLjgtMzkuOCA2LjItMTMuNCAxMy4yLTI2LjggMjAuNy0zOS45IDcuOC0xMy41IDE1LjgtMjYuMyAyNC4xLTM4LjIgMTQuOS0xLjMgMzAtMiA0NS4yLTIgMTUuMSAwIDMwLjIuNyA0NSAxLjkgOC4zIDExLjkgMTYuNCAyNC42IDI0LjIgMzggNy42IDEzLjEgMTQuNSAyNi40IDIwLjggMzkuOC02LjMgMTMuNC0xMy4yIDI2LjgtMjAuNyAzOS45em0zMi4zLTEzYzUuNCAxMy40IDEwIDI2LjggMTMuOCAzOS44LTEzLjEgMy4yLTI2LjkgNS45LTQxLjIgOCA0LjktNy43IDkuOC0xNS42IDE0LjQtMjMuNyA0LjYtOCA4LjktMTYuMSAxMy0yNC4xek00MjEuMiA0MzBjLTkuMy05LjYtMTguNi0yMC4zLTI3LjgtMzIgOSAuNCAxOC4yLjcgMjcuNS43IDkuNCAwIDE4LjctLjIgMjcuOC0uNy05IDExLjctMTguMyAyMi40LTI3LjUgMzJ6bS03NC40LTU4LjljLTE0LjItMi4xLTI3LjktNC43LTQxLTcuOSAzLjctMTIuOSA4LjMtMjYuMiAxMy41LTM5LjUgNC4xIDggOC40IDE2IDEzLjEgMjQgNC43IDggOS41IDE1LjggMTQuNCAyMy40ek00MjAuNyAxNjNjOS4zIDkuNiAxOC42IDIwLjMgMjcuOCAzMi05LS40LTE4LjItLjctMjcuNS0uNy05LjQgMC0xOC43LjItMjcuOC43IDktMTEuNyAxOC4zLTIyLjQgMjcuNS0zMnptLTc0IDU4LjljLTQuOSA3LjctOS44IDE1LjYtMTQuNCAyMy43LTQuNiA4LTguOSAxNi0xMyAyNC01LjQtMTMuNC0xMC0yNi44LTEzLjgtMzkuOCAxMy4xLTMuMSAyNi45LTUuOCA0MS4yLTcuOXptLTkwLjUgMTI1LjJjLTM1LjQtMTUuMS01OC4zLTM0LjktNTguMy01MC42IDAtMTUuNyAyMi45LTM1LjYgNTguMy01MC42IDguNi0zLjcgMTgtNyAyNy43LTEwLjEgNS43IDE5LjYgMTMuMiA0MCAyMi41IDYwLjktOS4yIDIwLjgtMTYuNiA0MS4xLTIyLjIgNjAuNi05LjktMy4xLTE5LjMtNi41LTI4LTEwLjJ6TTMxMCA0OTBjLTEzLjYtNy44LTE5LjUtMzcuNS0xNC45LTc1LjcgMS4xLTkuNCAyLjktMTkuMyA1LjEtMjkuNCAxOS42IDQuOCA0MSA4LjUgNjMuNSAxMC45IDEzLjUgMTguNSAyNy41IDM1LjMgNDEuNiA1MC0zMi42IDMwLjMtNjMuMiA0Ni45LTg0IDQ2LjktNC41LS4xLTguMy0xLTExLjMtMi43em0yMzcuMi03Ni4yYzQuNyAzOC4yLTEuMSA2Ny45LTE0LjYgNzUuOC0zIDEuOC02LjkgMi42LTExLjUgMi42LTIwLjcgMC01MS40LTE2LjUtODQtNDYuNiAxNC0xNC43IDI4LTMxLjQgNDEuMy00OS45IDIyLjYtMi40IDQ0LTYuMSA2My42LTExIDIuMyAxMC4xIDQuMSAxOS44IDUuMiAyOS4xem0zOC41LTY2LjdjLTguNiAzLjctMTggNy0yNy43IDEwLjEtNS43LTE5LjYtMTMuMi00MC0yMi41LTYwLjkgOS4yLTIwLjggMTYuNi00MS4xIDIyLjItNjAuNiA5LjkgMy4xIDE5LjMgNi41IDI4LjEgMTAuMiAzNS40IDE1LjEgNTguMyAzNC45IDU4LjMgNTAuNi0uMSAxNS43LTIzIDM1LjYtNTguNCA1MC42ek0zMjAuOCA3OC40eiIvPgogICAgPGNpcmNsZSBjeD0iNDIwLjkiIGN5PSIyOTYuNSIgcj0iNDUuNyIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-redo: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCBkPSJNMCAwaDI0djI0SDB6IiBmaWxsPSJub25lIi8+PHBhdGggZD0iTTE4LjQgMTAuNkMxNi41NSA4Ljk5IDE0LjE1IDggMTEuNSA4Yy00LjY1IDAtOC41OCAzLjAzLTkuOTYgNy4yMkwzLjkgMTZjMS4wNS0zLjE5IDQuMDUtNS41IDcuNi01LjUgMS45NSAwIDMuNzMuNzIgNS4xMiAxLjg4TDEzIDE2aDlWN2wtMy42IDMuNnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-refresh: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTkgMTMuNWMtMi40OSAwLTQuNS0yLjAxLTQuNS00LjVTNi41MSA0LjUgOSA0LjVjMS4yNCAwIDIuMzYuNTIgMy4xNyAxLjMzTDEwIDhoNVYzbC0xLjc2IDEuNzZDMTIuMTUgMy42OCAxMC42NiAzIDkgMyA1LjY5IDMgMy4wMSA1LjY5IDMuMDEgOVM1LjY5IDE1IDkgMTVjMi45NyAwIDUuNDMtMi4xNiA1LjktNWgtMS41MmMtLjQ2IDItMi4yNCAzLjUtNC4zOCAzLjV6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-regex: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi1hY2NlbnQyIiBmaWxsPSIjRkZGIj4KICAgIDxjaXJjbGUgY2xhc3M9InN0MiIgY3g9IjUuNSIgY3k9IjE0LjUiIHI9IjEuNSIvPgogICAgPHJlY3QgeD0iMTIiIHk9IjQiIGNsYXNzPSJzdDIiIHdpZHRoPSIxIiBoZWlnaHQ9IjgiLz4KICAgIDxyZWN0IHg9IjguNSIgeT0iNy41IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjg2NiAtMC41IDAuNSAwLjg2NiAtMi4zMjU1IDcuMzIxOSkiIGNsYXNzPSJzdDIiIHdpZHRoPSI4IiBoZWlnaHQ9IjEiLz4KICAgIDxyZWN0IHg9IjEyIiB5PSI0IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjUgLTAuODY2IDAuODY2IDAuNSAtMC42Nzc5IDE0LjgyNTIpIiBjbGFzcz0ic3QyIiB3aWR0aD0iMSIgaGVpZ2h0PSI4Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-run: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTggNXYxNGwxMS03eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-running: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMjU2IDhDMTE5IDggOCAxMTkgOCAyNTZzMTExIDI0OCAyNDggMjQ4IDI0OC0xMTEgMjQ4LTI0OFMzOTMgOCAyNTYgOHptOTYgMzI4YzAgOC44LTcuMiAxNi0xNiAxNkgxNzZjLTguOCAwLTE2LTcuMi0xNi0xNlYxNzZjMC04LjggNy4yLTE2IDE2LTE2aDE2MGM4LjggMCAxNiA3LjIgMTYgMTZ2MTYweiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-save: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE3IDNINWMtMS4xMSAwLTIgLjktMiAydjE0YzAgMS4xLjg5IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjdsLTQtNHptLTUgMTZjLTEuNjYgMC0zLTEuMzQtMy0zczEuMzQtMyAzLTMgMyAxLjM0IDMgMy0xLjM0IDMtMyAzem0zLTEwSDVWNWgxMHY0eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-search: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjEsMTAuOWgtMC43bC0wLjItMC4yYzAuOC0wLjksMS4zLTIuMiwxLjMtMy41YzAtMy0yLjQtNS40LTUuNC01LjRTMS44LDQuMiwxLjgsNy4xczIuNCw1LjQsNS40LDUuNCBjMS4zLDAsMi41LTAuNSwzLjUtMS4zbDAuMiwwLjJ2MC43bDQuMSw0LjFsMS4yLTEuMkwxMi4xLDEwLjl6IE03LjEsMTAuOWMtMi4xLDAtMy43LTEuNy0zLjctMy43czEuNy0zLjcsMy43LTMuN3MzLjcsMS43LDMuNywzLjcgUzkuMiwxMC45LDcuMSwxMC45eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-settings: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuNDMgMTIuOThjLjA0LS4zMi4wNy0uNjQuMDctLjk4cy0uMDMtLjY2LS4wNy0uOThsMi4xMS0xLjY1Yy4xOS0uMTUuMjQtLjQyLjEyLS42NGwtMi0zLjQ2Yy0uMTItLjIyLS4zOS0uMy0uNjEtLjIybC0yLjQ5IDFjLS41Mi0uNC0xLjA4LS43My0xLjY5LS45OGwtLjM4LTIuNjVBLjQ4OC40ODggMCAwMDE0IDJoLTRjLS4yNSAwLS40Ni4xOC0uNDkuNDJsLS4zOCAyLjY1Yy0uNjEuMjUtMS4xNy41OS0xLjY5Ljk4bC0yLjQ5LTFjLS4yMy0uMDktLjQ5IDAtLjYxLjIybC0yIDMuNDZjLS4xMy4yMi0uMDcuNDkuMTIuNjRsMi4xMSAxLjY1Yy0uMDQuMzItLjA3LjY1LS4wNy45OHMuMDMuNjYuMDcuOThsLTIuMTEgMS42NWMtLjE5LjE1LS4yNC40Mi0uMTIuNjRsMiAzLjQ2Yy4xMi4yMi4zOS4zLjYxLjIybDIuNDktMWMuNTIuNCAxLjA4LjczIDEuNjkuOThsLjM4IDIuNjVjLjAzLjI0LjI0LjQyLjQ5LjQyaDRjLjI1IDAgLjQ2LS4xOC40OS0uNDJsLjM4LTIuNjVjLjYxLS4yNSAxLjE3LS41OSAxLjY5LS45OGwyLjQ5IDFjLjIzLjA5LjQ5IDAgLjYxLS4yMmwyLTMuNDZjLjEyLS4yMi4wNy0uNDktLjEyLS42NGwtMi4xMS0xLjY1ek0xMiAxNS41Yy0xLjkzIDAtMy41LTEuNTctMy41LTMuNXMxLjU3LTMuNSAzLjUtMy41IDMuNSAxLjU3IDMuNSAzLjUtMS41NyAzLjUtMy41IDMuNXoiLz4KPC9zdmc+Cg==);
  --jp-icon-share: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTSAxOCAyIEMgMTYuMzU0OTkgMiAxNSAzLjM1NDk5MDQgMTUgNSBDIDE1IDUuMTkwOTUyOSAxNS4wMjE3OTEgNS4zNzcxMjI0IDE1LjA1NjY0MSA1LjU1ODU5MzggTCA3LjkyMTg3NSA5LjcyMDcwMzEgQyA3LjM5ODUzOTkgOS4yNzc4NTM5IDYuNzMyMDc3MSA5IDYgOSBDIDQuMzU0OTkwNCA5IDMgMTAuMzU0OTkgMyAxMiBDIDMgMTMuNjQ1MDEgNC4zNTQ5OTA0IDE1IDYgMTUgQyA2LjczMjA3NzEgMTUgNy4zOTg1Mzk5IDE0LjcyMjE0NiA3LjkyMTg3NSAxNC4yNzkyOTcgTCAxNS4wNTY2NDEgMTguNDM5NDUzIEMgMTUuMDIxNTU1IDE4LjYyMTUxNCAxNSAxOC44MDgzODYgMTUgMTkgQyAxNSAyMC42NDUwMSAxNi4zNTQ5OSAyMiAxOCAyMiBDIDE5LjY0NTAxIDIyIDIxIDIwLjY0NTAxIDIxIDE5IEMgMjEgMTcuMzU0OTkgMTkuNjQ1MDEgMTYgMTggMTYgQyAxNy4yNjc0OCAxNiAxNi42MDE1OTMgMTYuMjc5MzI4IDE2LjA3ODEyNSAxNi43MjI2NTYgTCA4Ljk0MzM1OTQgMTIuNTU4NTk0IEMgOC45NzgyMDk1IDEyLjM3NzEyMiA5IDEyLjE5MDk1MyA5IDEyIEMgOSAxMS44MDkwNDcgOC45NzgyMDk1IDExLjYyMjg3OCA4Ljk0MzM1OTQgMTEuNDQxNDA2IEwgMTYuMDc4MTI1IDcuMjc5Mjk2OSBDIDE2LjYwMTQ2IDcuNzIyMTQ2MSAxNy4yNjc5MjMgOCAxOCA4IEMgMTkuNjQ1MDEgOCAyMSA2LjY0NTAwOTYgMjEgNSBDIDIxIDMuMzU0OTkwNCAxOS42NDUwMSAyIDE4IDIgeiBNIDE4IDQgQyAxOC41NjQxMjkgNCAxOSA0LjQzNTg3MDYgMTkgNSBDIDE5IDUuNTY0MTI5NCAxOC41NjQxMjkgNiAxOCA2IEMgMTcuNDM1ODcxIDYgMTcgNS41NjQxMjk0IDE3IDUgQyAxNyA0LjQzNTg3MDYgMTcuNDM1ODcxIDQgMTggNCB6IE0gNiAxMSBDIDYuNTY0MTI5NCAxMSA3IDExLjQzNTg3MSA3IDEyIEMgNyAxMi41NjQxMjkgNi41NjQxMjk0IDEzIDYgMTMgQyA1LjQzNTg3MDYgMTMgNSAxMi41NjQxMjkgNSAxMiBDIDUgMTEuNDM1ODcxIDUuNDM1ODcwNiAxMSA2IDExIHogTSAxOCAxOCBDIDE4LjU2NDEyOSAxOCAxOSAxOC40MzU4NzEgMTkgMTkgQyAxOSAxOS41NjQxMjkgMTguNTY0MTI5IDIwIDE4IDIwIEMgMTcuNDM1ODcxIDIwIDE3IDE5LjU2NDEyOSAxNyAxOSBDIDE3IDE4LjQzNTg3MSAxNy40MzU4NzEgMTggMTggMTggeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-spreadsheet: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNENBRjUwIiBkPSJNMi4yIDIuMnYxNy42aDE3LjZWMi4ySDIuMnptMTUuNCA3LjdoLTUuNVY0LjRoNS41djUuNXpNOS45IDQuNHY1LjVINC40VjQuNGg1LjV6bS01LjUgNy43aDUuNXY1LjVINC40di01LjV6bTcuNyA1LjV2LTUuNWg1LjV2NS41aC01LjV6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-stop: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik02IDZoMTJ2MTJINnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-tab: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIxIDNIM2MtMS4xIDAtMiAuOS0yIDJ2MTRjMCAxLjEuOSAyIDIgMmgxOGMxLjEgMCAyLS45IDItMlY1YzAtMS4xLS45LTItMi0yem0wIDE2SDNWNWgxMHY0aDh2MTB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-table-rows: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMSw4SDNWNGgxOFY4eiBNMjEsMTBIM3Y0aDE4VjEweiBNMjEsMTZIM3Y0aDE4VjE2eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-tag: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjgiIGhlaWdodD0iMjgiIHZpZXdCb3g9IjAgMCA0MyAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTI4LjgzMzIgMTIuMzM0TDMyLjk5OTggMTYuNTAwN0wzNy4xNjY1IDEyLjMzNEgyOC44MzMyWiIvPgoJCTxwYXRoIGQ9Ik0xNi4yMDk1IDIxLjYxMDRDMTUuNjg3MyAyMi4xMjk5IDE0Ljg0NDMgMjIuMTI5OSAxNC4zMjQ4IDIxLjYxMDRMNi45ODI5IDE0LjcyNDVDNi41NzI0IDE0LjMzOTQgNi4wODMxMyAxMy42MDk4IDYuMDQ3ODYgMTMuMDQ4MkM1Ljk1MzQ3IDExLjUyODggNi4wMjAwMiA4LjYxOTQ0IDYuMDY2MjEgNy4wNzY5NUM2LjA4MjgxIDYuNTE0NzcgNi41NTU0OCA2LjA0MzQ3IDcuMTE4MDQgNi4wMzA1NUM5LjA4ODYzIDUuOTg0NzMgMTMuMjYzOCA1LjkzNTc5IDEzLjY1MTggNi4zMjQyNUwyMS43MzY5IDEzLjYzOUMyMi4yNTYgMTQuMTU4NSAyMS43ODUxIDE1LjQ3MjQgMjEuMjYyIDE1Ljk5NDZMMTYuMjA5NSAyMS42MTA0Wk05Ljc3NTg1IDguMjY1QzkuMzM1NTEgNy44MjU2NiA4LjYyMzUxIDcuODI1NjYgOC4xODI4IDguMjY1QzcuNzQzNDYgOC43MDU3MSA3Ljc0MzQ2IDkuNDE3MzMgOC4xODI4IDkuODU2NjdDOC42MjM4MiAxMC4yOTY0IDkuMzM1ODIgMTAuMjk2NCA5Ljc3NTg1IDkuODU2NjdDMTAuMjE1NiA5LjQxNzMzIDEwLjIxNTYgOC43MDUzMyA5Ljc3NTg1IDguMjY1WiIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-terminal: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0IiA+CiAgICA8cmVjdCBjbGFzcz0ianAtdGVybWluYWwtaWNvbi1iYWNrZ3JvdW5kLWNvbG9yIGpwLWljb24tc2VsZWN0YWJsZSIgd2lkdGg9IjIwIiBoZWlnaHQ9IjIwIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgyIDIpIiBmaWxsPSIjMzMzMzMzIi8+CiAgICA8cGF0aCBjbGFzcz0ianAtdGVybWluYWwtaWNvbi1jb2xvciBqcC1pY29uLXNlbGVjdGFibGUtaW52ZXJzZSIgZD0iTTUuMDU2NjQgOC43NjE3MkM1LjA1NjY0IDguNTk3NjYgNS4wMzEyNSA4LjQ1MzEyIDQuOTgwNDcgOC4zMjgxMkM0LjkzMzU5IDguMTk5MjIgNC44NTU0NyA4LjA4MjAzIDQuNzQ2MDkgNy45NzY1NkM0LjY0MDYyIDcuODcxMDkgNC41IDcuNzc1MzkgNC4zMjQyMiA3LjY4OTQ1QzQuMTUyMzQgNy41OTk2MSAzLjk0MzM2IDcuNTExNzIgMy42OTcyNyA3LjQyNTc4QzMuMzAyNzMgNy4yODUxNiAyLjk0MzM2IDcuMTM2NzIgMi42MTkxNCA2Ljk4MDQ3QzIuMjk0OTIgNi44MjQyMiAyLjAxNzU4IDYuNjQyNTggMS43ODcxMSA2LjQzNTU1QzEuNTYwNTUgNi4yMjg1MiAxLjM4NDc3IDUuOTg4MjggMS4yNTk3NyA1LjcxNDg0QzEuMTM0NzcgNS40Mzc1IDEuMDcyMjcgNS4xMDkzOCAxLjA3MjI3IDQuNzMwNDdDMS4wNzIyNyA0LjM5ODQ0IDEuMTI4OTEgNC4wOTU3IDEuMjQyMTkgMy44MjIyN0MxLjM1NTQ3IDMuNTQ0OTIgMS41MTU2MiAzLjMwNDY5IDEuNzIyNjYgMy4xMDE1NkMxLjkyOTY5IDIuODk4NDQgMi4xNzk2OSAyLjczNDM3IDIuNDcyNjYgMi42MDkzOEMyLjc2NTYyIDIuNDg0MzggMy4wOTE4IDIuNDA0MyAzLjQ1MTE3IDIuMzY5MTRWMS4xMDkzOEg0LjM4ODY3VjIuMzgwODZDNC43NDAyMyAyLjQyNzczIDUuMDU2NjQgMi41MjM0NCA1LjMzNzg5IDIuNjY3OTdDNS42MTkxNCAyLjgxMjUgNS44NTc0MiAzLjAwMTk1IDYuMDUyNzMgMy4yMzYzM0M2LjI1MTk1IDMuNDY2OCA2LjQwNDMgMy43NDAyMyA2LjUwOTc3IDQuMDU2NjRDNi42MTkxNCA0LjM2OTE0IDYuNjczODMgNC43MjA3IDYuNjczODMgNS4xMTEzM0g1LjA0NDkyQzUuMDQ0OTIgNC42Mzg2NyA0LjkzNzUgNC4yODEyNSA0LjcyMjY2IDQuMDM5MDZDNC41MDc4MSAzLjc5Mjk3IDQuMjE2OCAzLjY2OTkyIDMuODQ5NjEgMy42Njk5MkMzLjY1MDM5IDMuNjY5OTIgMy40NzY1NiAzLjY5NzI3IDMuMzI4MTIgMy43NTE5NUMzLjE4MzU5IDMuODAyNzMgMy4wNjQ0NSAzLjg3Njk1IDIuOTcwNyAzLjk3NDYxQzIuODc2OTUgNC4wNjgzNiAyLjgwNjY0IDQuMTc5NjkgMi43NTk3NyA0LjMwODU5QzIuNzE2OCA0LjQzNzUgMi42OTUzMSA0LjU3ODEyIDIuNjk1MzEgNC43MzA0N0MyLjY5NTMxIDQuODgyODEgMi43MTY4IDUuMDE5NTMgMi43NTk3NyA1LjE0MDYyQzIuODA2NjQgNS4yNTc4MSAyLjg4MjgxIDUuMzY3MTkgMi45ODgyOCA1LjQ2ODc1QzMuMDk3NjYgNS41NzAzMSAzLjI0MDIzIDUuNjY3OTcgMy40MTYwMiA1Ljc2MTcyQzMuNTkxOCA1Ljg1MTU2IDMuODEwNTUgNS45NDMzNiA0LjA3MjI3IDYuMDM3MTFDNC40NjY4IDYuMTg1NTUgNC44MjQyMiA2LjMzOTg0IDUuMTQ0NTMgNi41QzUuNDY0ODQgNi42NTYyNSA1LjczODI4IDYuODM5ODQgNS45NjQ4NCA3LjA1MDc4QzYuMTk1MzEgNy4yNTc4MSA2LjM3MTA5IDcuNSA2LjQ5MjE5IDcuNzc3MzRDNi42MTcxOSA4LjA1MDc4IDYuNjc5NjkgOC4zNzUgNi42Nzk2OSA4Ljc1QzYuNjc5NjkgOS4wOTM3NSA2LjYyMzA1IDkuNDA0MyA2LjUwOTc3IDkuNjgxNjRDNi4zOTY0OCA5Ljk1NTA4IDYuMjM0MzggMTAuMTkxNCA2LjAyMzQ0IDEwLjM5MDZDNS44MTI1IDEwLjU4OTggNS41NTg1OSAxMC43NSA1LjI2MTcyIDEwLjg3MTFDNC45NjQ4NCAxMC45ODgzIDQuNjMyODEgMTEuMDY0NSA0LjI2NTYyIDExLjA5OTZWMTIuMjQ4SDMuMzMzOThWMTEuMDk5NkMzLjAwMTk1IDExLjA2ODQgMi42Nzk2OSAxMC45OTYxIDIuMzY3MTkgMTAuODgyOEMyLjA1NDY5IDEwLjc2NTYgMS43NzczNCAxMC41OTc3IDEuNTM1MTYgMTAuMzc4OUMxLjI5Njg4IDEwLjE2MDIgMS4xMDU0NyA5Ljg4NDc3IDAuOTYwOTM4IDkuNTUyNzNDMC44MTY0MDYgOS4yMTY4IDAuNzQ0MTQxIDguODE0NDUgMC43NDQxNDEgOC4zNDU3SDIuMzc4OTFDMi4zNzg5MSA4LjYyNjk1IDIuNDE5OTIgOC44NjMyOCAyLjUwMTk1IDkuMDU0NjlDMi41ODM5OCA5LjI0MjE5IDIuNjg5NDUgOS4zOTI1OCAyLjgxODM2IDkuNTA1ODZDMi45NTExNyA5LjYxNTIzIDMuMTAxNTYgOS42OTMzNiAzLjI2OTUzIDkuNzQwMjNDMy40Mzc1IDkuNzg3MTEgMy42MDkzOCA5LjgxMDU1IDMuNzg1MTYgOS44MTA1NUM0LjIwMzEyIDkuODEwNTUgNC41MTk1MyA5LjcxMjg5IDQuNzM0MzggOS41MTc1OEM0Ljk0OTIyIDkuMzIyMjcgNS4wNTY2NCA5LjA3MDMxIDUuMDU2NjQgOC43NjE3MlpNMTMuNDE4IDEyLjI3MTVIOC4wNzQyMlYxMUgxMy40MThWMTIuMjcxNVoiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDMuOTUyNjQgNikiIGZpbGw9IndoaXRlIi8+Cjwvc3ZnPgo=);
  --jp-icon-text-editor: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtdGV4dC1lZGl0b3ItaWNvbi1jb2xvciBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xNSAxNUgzdjJoMTJ2LTJ6bTAtOEgzdjJoMTJWN3pNMyAxM2gxOHYtMkgzdjJ6bTAgOGgxOHYtMkgzdjJ6TTMgM3YyaDE4VjNIM3oiLz4KPC9zdmc+Cg==);
  --jp-icon-toc: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik03LDVIMjFWN0g3VjVNNywxM1YxMUgyMVYxM0g3TTQsNC41QTEuNSwxLjUgMCAwLDEgNS41LDZBMS41LDEuNSAwIDAsMSA0LDcuNUExLjUsMS41IDAgMCwxIDIuNSw2QTEuNSwxLjUgMCAwLDEgNCw0LjVNNCwxMC41QTEuNSwxLjUgMCAwLDEgNS41LDEyQTEuNSwxLjUgMCAwLDEgNCwxMy41QTEuNSwxLjUgMCAwLDEgMi41LDEyQTEuNSwxLjUgMCAwLDEgNCwxMC41TTcsMTlWMTdIMjFWMTlIN000LDE2LjVBMS41LDEuNSAwIDAsMSA1LjUsMThBMS41LDEuNSAwIDAsMSA0LDE5LjVBMS41LDEuNSAwIDAsMSAyLjUsMThBMS41LDEuNSAwIDAsMSA0LDE2LjVaIiAvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-tree-view: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMiAxMVYzaC03djNIOVYzSDJ2OGg3VjhoMnYxMGg0djNoN3YtOGgtN3YzaC0yVjhoMnYzeiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMiAxNy4xODQ0IDIuOTY5NjggMTQuMzAzMiAxLjg2MDk0IDExLjQ0MDlaIi8+CiAgICA8cGF0aCBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiMzMzMzMzMiIHN0cm9rZT0iIzMzMzMzMyIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOCA5Ljg2NzE5KSIgZD0iTTIuODYwMTUgNC44NjUzNUwwLjcyNjU0OSAyLjk5OTU5TDAgMy42MzA0NUwyLjg2MDE1IDYuMTMxNTdMOCAwLjYzMDg3Mkw3LjI3ODU3IDBMMi44NjAxNSA0Ljg2NTM1WiIvPgo8L3N2Zz4K);
  --jp-icon-undo: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjUgOGMtMi42NSAwLTUuMDUuOTktNi45IDIuNkwyIDd2OWg5bC0zLjYyLTMuNjJjMS4zOS0xLjE2IDMuMTYtMS44OCA1LjEyLTEuODggMy41NCAwIDYuNTUgMi4zMSA3LjYgNS41bDIuMzctLjc4QzIxLjA4IDExLjAzIDE3LjE1IDggMTIuNSA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-user: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE2IDdhNCA0IDAgMTEtOCAwIDQgNCAwIDAxOCAwek0xMiAxNGE3IDcgMCAwMC03IDdoMTRhNyA3IDAgMDAtNy03eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-users: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZlcnNpb249IjEuMSIgdmlld0JveD0iMCAwIDM2IDI0IiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPgogPGcgY2xhc3M9ImpwLWljb24zIiB0cmFuc2Zvcm09Im1hdHJpeCgxLjczMjcgMCAwIDEuNzMyNyAtMy42MjgyIC4wOTk1NzcpIiBmaWxsPSIjNjE2MTYxIj4KICA8cGF0aCB0cmFuc2Zvcm09Im1hdHJpeCgxLjUsMCwwLDEuNSwwLC02KSIgZD0ibTEyLjE4NiA3LjUwOThjLTEuMDUzNSAwLTEuOTc1NyAwLjU2NjUtMi40Nzg1IDEuNDEwMiAwLjc1MDYxIDAuMzEyNzcgMS4zOTc0IDAuODI2NDggMS44NzMgMS40NzI3aDMuNDg2M2MwLTEuNTkyLTEuMjg4OS0yLjg4MjgtMi44ODA5LTIuODgyOHoiLz4KICA8cGF0aCBkPSJtMjAuNDY1IDIuMzg5NWEyLjE4ODUgMi4xODg1IDAgMCAxLTIuMTg4NCAyLjE4ODUgMi4xODg1IDIuMTg4NSAwIDAgMS0yLjE4ODUtMi4xODg1IDIuMTg4NSAyLjE4ODUgMCAwIDEgMi4xODg1LTIuMTg4NSAyLjE4ODUgMi4xODg1IDAgMCAxIDIuMTg4NCAyLjE4ODV6Ii8+CiAgPHBhdGggdHJhbnNmb3JtPSJtYXRyaXgoMS41LDAsMCwxLjUsMCwtNikiIGQ9Im0zLjU4OTggOC40MjE5Yy0xLjExMjYgMC0yLjAxMzcgMC45MDExMS0yLjAxMzcgMi4wMTM3aDIuODE0NWMwLjI2Nzk3LTAuMzczMDkgMC41OTA3LTAuNzA0MzUgMC45NTg5OC0wLjk3ODUyLTAuMzQ0MzMtMC42MTY4OC0xLjAwMzEtMS4wMzUyLTEuNzU5OC0xLjAzNTJ6Ii8+CiAgPHBhdGggZD0ibTYuOTE1NCA0LjYyM2ExLjUyOTQgMS41Mjk0IDAgMCAxLTEuNTI5NCAxLjUyOTQgMS41Mjk0IDEuNTI5NCAwIDAgMS0xLjUyOTQtMS41Mjk0IDEuNTI5NCAxLjUyOTQgMCAwIDEgMS41Mjk0LTEuNTI5NCAxLjUyOTQgMS41Mjk0IDAgMCAxIDEuNTI5NCAxLjUyOTR6Ii8+CiAgPHBhdGggZD0ibTYuMTM1IDEzLjUzNWMwLTMuMjM5MiAyLjYyNTktNS44NjUgNS44NjUtNS44NjUgMy4yMzkyIDAgNS44NjUgMi42MjU5IDUuODY1IDUuODY1eiIvPgogIDxjaXJjbGUgY3g9IjEyIiBjeT0iMy43Njg1IiByPSIyLjk2ODUiLz4KIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-vega: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbjEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjEyMTIxIj4KICAgIDxwYXRoIGQ9Ik0xMC42IDUuNGwyLjItMy4ySDIuMnY3LjNsNC02LjZ6Ii8+CiAgICA8cGF0aCBkPSJNMTUuOCAyLjJsLTQuNCA2LjZMNyA2LjNsLTQuOCA4djUuNWgxNy42VjIuMmgtNHptLTcgMTUuNEg1LjV2LTQuNGgzLjN2NC40em00LjQgMEg5LjhWOS44aDMuNHY3Ljh6bTQuNCAwaC0zLjRWNi41aDMuNHYxMS4xeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-word: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KIDxnIGNsYXNzPSJqcC1pY29uMiIgZmlsbD0iIzQxNDE0MSI+CiAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiA8L2c+CiA8ZyBjbGFzcz0ianAtaWNvbi1hY2NlbnQyIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSguNDMgLjA0MDEpIiBmaWxsPSIjZmZmIj4KICA8cGF0aCBkPSJtNC4xNCA4Ljc2cTAuMDY4Mi0xLjg5IDIuNDItMS44OSAxLjE2IDAgMS42OCAwLjQyIDAuNTY3IDAuNDEgMC41NjcgMS4xNnYzLjQ3cTAgMC40NjIgMC41MTQgMC40NjIgMC4xMDMgMCAwLjItMC4wMjMxdjAuNzE0cS0wLjM5OSAwLjEwMy0wLjY1MSAwLjEwMy0wLjQ1MiAwLTAuNjkzLTAuMjItMC4yMzEtMC4yLTAuMjg0LTAuNjYyLTAuOTU2IDAuODcyLTIgMC44NzItMC45MDMgMC0xLjQ3LTAuNDcyLTAuNTI1LTAuNDcyLTAuNTI1LTEuMjYgMC0wLjI2MiAwLjA0NTItMC40NzIgMC4wNTY3LTAuMjIgMC4xMTYtMC4zNzggMC4wNjgyLTAuMTY4IDAuMjMxLTAuMzA0IDAuMTU4LTAuMTQ3IDAuMjYyLTAuMjQyIDAuMTE2LTAuMDkxNCAwLjM2OC0wLjE2OCAwLjI2Mi0wLjA5MTQgMC4zOTktMC4xMjYgMC4xMzYtMC4wNDUyIDAuNDcyLTAuMTAzIDAuMzM2LTAuMDU3OCAwLjUwNC0wLjA3OTggMC4xNTgtMC4wMjMxIDAuNTY3LTAuMDc5OCAwLjU1Ni0wLjA2ODIgMC43NzctMC4yMjEgMC4yMi0wLjE1MiAwLjIyLTAuNDQxdi0wLjI1MnEwLTAuNDMtMC4zNTctMC42NjItMC4zMzYtMC4yMzEtMC45NzYtMC4yMzEtMC42NjIgMC0wLjk5OCAwLjI2Mi0wLjMzNiAwLjI1Mi0wLjM5OSAwLjc5OHptMS44OSAzLjY4cTAuNzg4IDAgMS4yNi0wLjQxIDAuNTA0LTAuNDIgMC41MDQtMC45MDN2LTEuMDVxLTAuMjg0IDAuMTM2LTAuODYxIDAuMjMxLTAuNTY3IDAuMDkxNC0wLjk4NyAwLjE1OC0wLjQyIDAuMDY4Mi0wLjc2NiAwLjMyNi0wLjMzNiAwLjI1Mi0wLjMzNiAwLjcwNHQwLjMwNCAwLjcwNCAwLjg2MSAwLjI1MnoiIHN0cm9rZS13aWR0aD0iMS4wNSIvPgogIDxwYXRoIGQ9Im0xMCA0LjU2aDAuOTQ1djMuMTVxMC42NTEtMC45NzYgMS44OS0wLjk3NiAxLjE2IDAgMS44OSAwLjg0IDAuNjgyIDAuODQgMC42ODIgMi4zMSAwIDEuNDctMC43MDQgMi40Mi0wLjcwNCAwLjg4Mi0xLjg5IDAuODgyLTEuMjYgMC0xLjg5LTEuMDJ2MC43NjZoLTAuODV6bTIuNjIgMy4wNHEtMC43NDYgMC0xLjE2IDAuNjQtMC40NTIgMC42My0wLjQ1MiAxLjY4IDAgMS4wNSAwLjQ1MiAxLjY4dDEuMTYgMC42M3EwLjc3NyAwIDEuMjYtMC42MyAwLjQ5NC0wLjY0IDAuNDk0LTEuNjggMC0xLjA1LTAuNDcyLTEuNjgtMC40NjItMC42NC0xLjI2LTAuNjR6IiBzdHJva2Utd2lkdGg9IjEuMDUiLz4KICA8cGF0aCBkPSJtMi43MyAxNS44IDEzLjYgMC4wMDgxYzAuMDA2OSAwIDAtMi42IDAtMi42IDAtMC4wMDc4LTEuMTUgMC0xLjE1IDAtMC4wMDY5IDAtMC4wMDgzIDEuNS0wLjAwODMgMS41LTJlLTMgLTAuMDAxNC0xMS4zLTAuMDAxNC0xMS4zLTAuMDAxNGwtMC4wMDU5Mi0xLjVjMC0wLjAwNzgtMS4xNyAwLjAwMTMtMS4xNyAwLjAwMTN6IiBzdHJva2Utd2lkdGg9Ii45NzUiLz4KIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-yaml: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1jb250cmFzdDIganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjRDgxQjYwIj4KICAgIDxwYXRoIGQ9Ik03LjIgMTguNnYtNS40TDMgNS42aDMuM2wxLjQgMy4xYy4zLjkuNiAxLjYgMSAyLjUuMy0uOC42LTEuNiAxLTIuNWwxLjQtMy4xaDMuNGwtNC40IDcuNnY1LjVsLTIuOS0uMXoiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxNi41IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxMSIgcj0iMi4xIi8+CiAgPC9nPgo8L3N2Zz4K);
}

/* Icon CSS class declarations */

.jp-AddAboveIcon {
  background-image: var(--jp-icon-add-above);
}

.jp-AddBelowIcon {
  background-image: var(--jp-icon-add-below);
}

.jp-AddIcon {
  background-image: var(--jp-icon-add);
}

.jp-BellIcon {
  background-image: var(--jp-icon-bell);
}

.jp-BugDotIcon {
  background-image: var(--jp-icon-bug-dot);
}

.jp-BugIcon {
  background-image: var(--jp-icon-bug);
}

.jp-BuildIcon {
  background-image: var(--jp-icon-build);
}

.jp-CaretDownEmptyIcon {
  background-image: var(--jp-icon-caret-down-empty);
}

.jp-CaretDownEmptyThinIcon {
  background-image: var(--jp-icon-caret-down-empty-thin);
}

.jp-CaretDownIcon {
  background-image: var(--jp-icon-caret-down);
}

.jp-CaretLeftIcon {
  background-image: var(--jp-icon-caret-left);
}

.jp-CaretRightIcon {
  background-image: var(--jp-icon-caret-right);
}

.jp-CaretUpEmptyThinIcon {
  background-image: var(--jp-icon-caret-up-empty-thin);
}

.jp-CaretUpIcon {
  background-image: var(--jp-icon-caret-up);
}

.jp-CaseSensitiveIcon {
  background-image: var(--jp-icon-case-sensitive);
}

.jp-CheckIcon {
  background-image: var(--jp-icon-check);
}

.jp-CircleEmptyIcon {
  background-image: var(--jp-icon-circle-empty);
}

.jp-CircleIcon {
  background-image: var(--jp-icon-circle);
}

.jp-ClearIcon {
  background-image: var(--jp-icon-clear);
}

.jp-CloseIcon {
  background-image: var(--jp-icon-close);
}

.jp-CodeCheckIcon {
  background-image: var(--jp-icon-code-check);
}

.jp-CodeIcon {
  background-image: var(--jp-icon-code);
}

.jp-CollapseAllIcon {
  background-image: var(--jp-icon-collapse-all);
}

.jp-ConsoleIcon {
  background-image: var(--jp-icon-console);
}

.jp-CopyIcon {
  background-image: var(--jp-icon-copy);
}

.jp-CopyrightIcon {
  background-image: var(--jp-icon-copyright);
}

.jp-CutIcon {
  background-image: var(--jp-icon-cut);
}

.jp-DeleteIcon {
  background-image: var(--jp-icon-delete);
}

.jp-DownloadIcon {
  background-image: var(--jp-icon-download);
}

.jp-DuplicateIcon {
  background-image: var(--jp-icon-duplicate);
}

.jp-EditIcon {
  background-image: var(--jp-icon-edit);
}

.jp-EllipsesIcon {
  background-image: var(--jp-icon-ellipses);
}

.jp-ErrorIcon {
  background-image: var(--jp-icon-error);
}

.jp-ExpandAllIcon {
  background-image: var(--jp-icon-expand-all);
}

.jp-ExtensionIcon {
  background-image: var(--jp-icon-extension);
}

.jp-FastForwardIcon {
  background-image: var(--jp-icon-fast-forward);
}

.jp-FileIcon {
  background-image: var(--jp-icon-file);
}

.jp-FileUploadIcon {
  background-image: var(--jp-icon-file-upload);
}

.jp-FilterDotIcon {
  background-image: var(--jp-icon-filter-dot);
}

.jp-FilterIcon {
  background-image: var(--jp-icon-filter);
}

.jp-FilterListIcon {
  background-image: var(--jp-icon-filter-list);
}

.jp-FolderFavoriteIcon {
  background-image: var(--jp-icon-folder-favorite);
}

.jp-FolderIcon {
  background-image: var(--jp-icon-folder);
}

.jp-HomeIcon {
  background-image: var(--jp-icon-home);
}

.jp-Html5Icon {
  background-image: var(--jp-icon-html5);
}

.jp-ImageIcon {
  background-image: var(--jp-icon-image);
}

.jp-InfoIcon {
  background-image: var(--jp-icon-info);
}

.jp-InspectorIcon {
  background-image: var(--jp-icon-inspector);
}

.jp-JsonIcon {
  background-image: var(--jp-icon-json);
}

.jp-JuliaIcon {
  background-image: var(--jp-icon-julia);
}

.jp-JupyterFaviconIcon {
  background-image: var(--jp-icon-jupyter-favicon);
}

.jp-JupyterIcon {
  background-image: var(--jp-icon-jupyter);
}

.jp-JupyterlabWordmarkIcon {
  background-image: var(--jp-icon-jupyterlab-wordmark);
}

.jp-KernelIcon {
  background-image: var(--jp-icon-kernel);
}

.jp-KeyboardIcon {
  background-image: var(--jp-icon-keyboard);
}

.jp-LaunchIcon {
  background-image: var(--jp-icon-launch);
}

.jp-LauncherIcon {
  background-image: var(--jp-icon-launcher);
}

.jp-LineFormIcon {
  background-image: var(--jp-icon-line-form);
}

.jp-LinkIcon {
  background-image: var(--jp-icon-link);
}

.jp-ListIcon {
  background-image: var(--jp-icon-list);
}

.jp-MarkdownIcon {
  background-image: var(--jp-icon-markdown);
}

.jp-MoveDownIcon {
  background-image: var(--jp-icon-move-down);
}

.jp-MoveUpIcon {
  background-image: var(--jp-icon-move-up);
}

.jp-NewFolderIcon {
  background-image: var(--jp-icon-new-folder);
}

.jp-NotTrustedIcon {
  background-image: var(--jp-icon-not-trusted);
}

.jp-NotebookIcon {
  background-image: var(--jp-icon-notebook);
}

.jp-NumberingIcon {
  background-image: var(--jp-icon-numbering);
}

.jp-OfflineBoltIcon {
  background-image: var(--jp-icon-offline-bolt);
}

.jp-PaletteIcon {
  background-image: var(--jp-icon-palette);
}

.jp-PasteIcon {
  background-image: var(--jp-icon-paste);
}

.jp-PdfIcon {
  background-image: var(--jp-icon-pdf);
}

.jp-PythonIcon {
  background-image: var(--jp-icon-python);
}

.jp-RKernelIcon {
  background-image: var(--jp-icon-r-kernel);
}

.jp-ReactIcon {
  background-image: var(--jp-icon-react);
}

.jp-RedoIcon {
  background-image: var(--jp-icon-redo);
}

.jp-RefreshIcon {
  background-image: var(--jp-icon-refresh);
}

.jp-RegexIcon {
  background-image: var(--jp-icon-regex);
}

.jp-RunIcon {
  background-image: var(--jp-icon-run);
}

.jp-RunningIcon {
  background-image: var(--jp-icon-running);
}

.jp-SaveIcon {
  background-image: var(--jp-icon-save);
}

.jp-SearchIcon {
  background-image: var(--jp-icon-search);
}

.jp-SettingsIcon {
  background-image: var(--jp-icon-settings);
}

.jp-ShareIcon {
  background-image: var(--jp-icon-share);
}

.jp-SpreadsheetIcon {
  background-image: var(--jp-icon-spreadsheet);
}

.jp-StopIcon {
  background-image: var(--jp-icon-stop);
}

.jp-TabIcon {
  background-image: var(--jp-icon-tab);
}

.jp-TableRowsIcon {
  background-image: var(--jp-icon-table-rows);
}

.jp-TagIcon {
  background-image: var(--jp-icon-tag);
}

.jp-TerminalIcon {
  background-image: var(--jp-icon-terminal);
}

.jp-TextEditorIcon {
  background-image: var(--jp-icon-text-editor);
}

.jp-TocIcon {
  background-image: var(--jp-icon-toc);
}

.jp-TreeViewIcon {
  background-image: var(--jp-icon-tree-view);
}

.jp-TrustedIcon {
  background-image: var(--jp-icon-trusted);
}

.jp-UndoIcon {
  background-image: var(--jp-icon-undo);
}

.jp-UserIcon {
  background-image: var(--jp-icon-user);
}

.jp-UsersIcon {
  background-image: var(--jp-icon-users);
}

.jp-VegaIcon {
  background-image: var(--jp-icon-vega);
}

.jp-WordIcon {
  background-image: var(--jp-icon-word);
}

.jp-YamlIcon {
  background-image: var(--jp-icon-yaml);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * (DEPRECATED) Support for consuming icons as CSS background images
 */

.jp-Icon,
.jp-MaterialIcon {
  background-position: center;
  background-repeat: no-repeat;
  background-size: 16px;
  min-width: 16px;
  min-height: 16px;
}

.jp-Icon-cover {
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

/**
 * (DEPRECATED) Support for specific CSS icon sizes
 */

.jp-Icon-16 {
  background-size: 16px;
  min-width: 16px;
  min-height: 16px;
}

.jp-Icon-18 {
  background-size: 18px;
  min-width: 18px;
  min-height: 18px;
}

.jp-Icon-20 {
  background-size: 20px;
  min-width: 20px;
  min-height: 20px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.lm-TabBar .lm-TabBar-addButton {
  align-items: center;
  display: flex;
  padding: 4px;
  padding-bottom: 5px;
  margin-right: 1px;
  background-color: var(--jp-layout-color2);
}

.lm-TabBar .lm-TabBar-addButton:hover {
  background-color: var(--jp-layout-color1);
}

.lm-DockPanel-tabBar .lm-TabBar-tab {
  width: var(--jp-private-horizontal-tab-width);
}

.lm-DockPanel-tabBar .lm-TabBar-content {
  flex: unset;
}

.lm-DockPanel-tabBar[data-orientation='horizontal'] {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * Support for icons as inline SVG HTMLElements
 */

/* recolor the primary elements of an icon */
.jp-icon0[fill] {
  fill: var(--jp-inverse-layout-color0);
}

.jp-icon1[fill] {
  fill: var(--jp-inverse-layout-color1);
}

.jp-icon2[fill] {
  fill: var(--jp-inverse-layout-color2);
}

.jp-icon3[fill] {
  fill: var(--jp-inverse-layout-color3);
}

.jp-icon4[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon0[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}

.jp-icon1[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}

.jp-icon2[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}

.jp-icon3[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}

.jp-icon4[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/* recolor the accent elements of an icon */
.jp-icon-accent0[fill] {
  fill: var(--jp-layout-color0);
}

.jp-icon-accent1[fill] {
  fill: var(--jp-layout-color1);
}

.jp-icon-accent2[fill] {
  fill: var(--jp-layout-color2);
}

.jp-icon-accent3[fill] {
  fill: var(--jp-layout-color3);
}

.jp-icon-accent4[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-accent0[stroke] {
  stroke: var(--jp-layout-color0);
}

.jp-icon-accent1[stroke] {
  stroke: var(--jp-layout-color1);
}

.jp-icon-accent2[stroke] {
  stroke: var(--jp-layout-color2);
}

.jp-icon-accent3[stroke] {
  stroke: var(--jp-layout-color3);
}

.jp-icon-accent4[stroke] {
  stroke: var(--jp-layout-color4);
}

/* set the color of an icon to transparent */
.jp-icon-none[fill] {
  fill: none;
}

.jp-icon-none[stroke] {
  stroke: none;
}

/* brand icon colors. Same for light and dark */
.jp-icon-brand0[fill] {
  fill: var(--jp-brand-color0);
}

.jp-icon-brand1[fill] {
  fill: var(--jp-brand-color1);
}

.jp-icon-brand2[fill] {
  fill: var(--jp-brand-color2);
}

.jp-icon-brand3[fill] {
  fill: var(--jp-brand-color3);
}

.jp-icon-brand4[fill] {
  fill: var(--jp-brand-color4);
}

.jp-icon-brand0[stroke] {
  stroke: var(--jp-brand-color0);
}

.jp-icon-brand1[stroke] {
  stroke: var(--jp-brand-color1);
}

.jp-icon-brand2[stroke] {
  stroke: var(--jp-brand-color2);
}

.jp-icon-brand3[stroke] {
  stroke: var(--jp-brand-color3);
}

.jp-icon-brand4[stroke] {
  stroke: var(--jp-brand-color4);
}

/* warn icon colors. Same for light and dark */
.jp-icon-warn0[fill] {
  fill: var(--jp-warn-color0);
}

.jp-icon-warn1[fill] {
  fill: var(--jp-warn-color1);
}

.jp-icon-warn2[fill] {
  fill: var(--jp-warn-color2);
}

.jp-icon-warn3[fill] {
  fill: var(--jp-warn-color3);
}

.jp-icon-warn0[stroke] {
  stroke: var(--jp-warn-color0);
}

.jp-icon-warn1[stroke] {
  stroke: var(--jp-warn-color1);
}

.jp-icon-warn2[stroke] {
  stroke: var(--jp-warn-color2);
}

.jp-icon-warn3[stroke] {
  stroke: var(--jp-warn-color3);
}

/* icon colors that contrast well with each other and most backgrounds */
.jp-icon-contrast0[fill] {
  fill: var(--jp-icon-contrast-color0);
}

.jp-icon-contrast1[fill] {
  fill: var(--jp-icon-contrast-color1);
}

.jp-icon-contrast2[fill] {
  fill: var(--jp-icon-contrast-color2);
}

.jp-icon-contrast3[fill] {
  fill: var(--jp-icon-contrast-color3);
}

.jp-icon-contrast0[stroke] {
  stroke: var(--jp-icon-contrast-color0);
}

.jp-icon-contrast1[stroke] {
  stroke: var(--jp-icon-contrast-color1);
}

.jp-icon-contrast2[stroke] {
  stroke: var(--jp-icon-contrast-color2);
}

.jp-icon-contrast3[stroke] {
  stroke: var(--jp-icon-contrast-color3);
}

.jp-icon-dot[fill] {
  fill: var(--jp-warn-color0);
}

.jp-jupyter-icon-color[fill] {
  fill: var(--jp-jupyter-icon-color, var(--jp-warn-color0));
}

.jp-notebook-icon-color[fill] {
  fill: var(--jp-notebook-icon-color, var(--jp-warn-color0));
}

.jp-json-icon-color[fill] {
  fill: var(--jp-json-icon-color, var(--jp-warn-color1));
}

.jp-console-icon-color[fill] {
  fill: var(--jp-console-icon-color, white);
}

.jp-console-icon-background-color[fill] {
  fill: var(--jp-console-icon-background-color, var(--jp-brand-color1));
}

.jp-terminal-icon-color[fill] {
  fill: var(--jp-terminal-icon-color, var(--jp-layout-color2));
}

.jp-terminal-icon-background-color[fill] {
  fill: var(
    --jp-terminal-icon-background-color,
    var(--jp-inverse-layout-color2)
  );
}

.jp-text-editor-icon-color[fill] {
  fill: var(--jp-text-editor-icon-color, var(--jp-inverse-layout-color3));
}

.jp-inspector-icon-color[fill] {
  fill: var(--jp-inspector-icon-color, var(--jp-inverse-layout-color3));
}

/* CSS for icons in selected filebrowser listing items */
.jp-DirListing-item.jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}

.jp-DirListing-item.jp-mod-selected .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}

/* stylelint-disable selector-max-class, selector-max-compound-selectors */

/**
* TODO: come up with non css-hack solution for showing the busy icon on top
*  of the close icon
* CSS for complex behavior of close icon of tabs in the main area tabbar
*/
.lm-DockPanel-tabBar
  .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon3[fill] {
  fill: none;
}

.lm-DockPanel-tabBar
  .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: var(--jp-inverse-layout-color3);
}

/* stylelint-enable selector-max-class, selector-max-compound-selectors */

/* CSS for icons in status bar */
#jp-main-statusbar .jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}

#jp-main-statusbar .jp-mod-selected .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}

/* special handling for splash icon CSS. While the theme CSS reloads during
   splash, the splash icon can loose theming. To prevent that, we set a
   default for its color variable */
:root {
  --jp-warn-color0: var(--md-orange-700);
}

/* not sure what to do with this one, used in filebrowser listing */
.jp-DragIcon {
  margin-right: 4px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * Support for alt colors for icons as inline SVG HTMLElements
 */

/* alt recolor the primary elements of an icon */
.jp-icon-alt .jp-icon0[fill] {
  fill: var(--jp-layout-color0);
}

.jp-icon-alt .jp-icon1[fill] {
  fill: var(--jp-layout-color1);
}

.jp-icon-alt .jp-icon2[fill] {
  fill: var(--jp-layout-color2);
}

.jp-icon-alt .jp-icon3[fill] {
  fill: var(--jp-layout-color3);
}

.jp-icon-alt .jp-icon4[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-alt .jp-icon0[stroke] {
  stroke: var(--jp-layout-color0);
}

.jp-icon-alt .jp-icon1[stroke] {
  stroke: var(--jp-layout-color1);
}

.jp-icon-alt .jp-icon2[stroke] {
  stroke: var(--jp-layout-color2);
}

.jp-icon-alt .jp-icon3[stroke] {
  stroke: var(--jp-layout-color3);
}

.jp-icon-alt .jp-icon4[stroke] {
  stroke: var(--jp-layout-color4);
}

/* alt recolor the accent elements of an icon */
.jp-icon-alt .jp-icon-accent0[fill] {
  fill: var(--jp-inverse-layout-color0);
}

.jp-icon-alt .jp-icon-accent1[fill] {
  fill: var(--jp-inverse-layout-color1);
}

.jp-icon-alt .jp-icon-accent2[fill] {
  fill: var(--jp-inverse-layout-color2);
}

.jp-icon-alt .jp-icon-accent3[fill] {
  fill: var(--jp-inverse-layout-color3);
}

.jp-icon-alt .jp-icon-accent4[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-alt .jp-icon-accent0[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}

.jp-icon-alt .jp-icon-accent1[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}

.jp-icon-alt .jp-icon-accent2[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}

.jp-icon-alt .jp-icon-accent3[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}

.jp-icon-alt .jp-icon-accent4[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-icon-hoverShow:not(:hover) .jp-icon-hoverShow-content {
  display: none !important;
}

/**
 * Support for hover colors for icons as inline SVG HTMLElements
 */

/**
 * regular colors
 */

/* recolor the primary elements of an icon */
.jp-icon-hover :hover .jp-icon0-hover[fill] {
  fill: var(--jp-inverse-layout-color0);
}

.jp-icon-hover :hover .jp-icon1-hover[fill] {
  fill: var(--jp-inverse-layout-color1);
}

.jp-icon-hover :hover .jp-icon2-hover[fill] {
  fill: var(--jp-inverse-layout-color2);
}

.jp-icon-hover :hover .jp-icon3-hover[fill] {
  fill: var(--jp-inverse-layout-color3);
}

.jp-icon-hover :hover .jp-icon4-hover[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-hover :hover .jp-icon0-hover[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}

.jp-icon-hover :hover .jp-icon1-hover[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}

.jp-icon-hover :hover .jp-icon2-hover[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}

.jp-icon-hover :hover .jp-icon3-hover[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}

.jp-icon-hover :hover .jp-icon4-hover[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/* recolor the accent elements of an icon */
.jp-icon-hover :hover .jp-icon-accent0-hover[fill] {
  fill: var(--jp-layout-color0);
}

.jp-icon-hover :hover .jp-icon-accent1-hover[fill] {
  fill: var(--jp-layout-color1);
}

.jp-icon-hover :hover .jp-icon-accent2-hover[fill] {
  fill: var(--jp-layout-color2);
}

.jp-icon-hover :hover .jp-icon-accent3-hover[fill] {
  fill: var(--jp-layout-color3);
}

.jp-icon-hover :hover .jp-icon-accent4-hover[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-hover :hover .jp-icon-accent0-hover[stroke] {
  stroke: var(--jp-layout-color0);
}

.jp-icon-hover :hover .jp-icon-accent1-hover[stroke] {
  stroke: var(--jp-layout-color1);
}

.jp-icon-hover :hover .jp-icon-accent2-hover[stroke] {
  stroke: var(--jp-layout-color2);
}

.jp-icon-hover :hover .jp-icon-accent3-hover[stroke] {
  stroke: var(--jp-layout-color3);
}

.jp-icon-hover :hover .jp-icon-accent4-hover[stroke] {
  stroke: var(--jp-layout-color4);
}

/* set the color of an icon to transparent */
.jp-icon-hover :hover .jp-icon-none-hover[fill] {
  fill: none;
}

.jp-icon-hover :hover .jp-icon-none-hover[stroke] {
  stroke: none;
}

/**
 * inverse colors
 */

/* inverse recolor the primary elements of an icon */
.jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[fill] {
  fill: var(--jp-layout-color0);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[fill] {
  fill: var(--jp-layout-color1);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[fill] {
  fill: var(--jp-layout-color2);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[fill] {
  fill: var(--jp-layout-color3);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[stroke] {
  stroke: var(--jp-layout-color0);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[stroke] {
  stroke: var(--jp-layout-color1);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[stroke] {
  stroke: var(--jp-layout-color2);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[stroke] {
  stroke: var(--jp-layout-color3);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[stroke] {
  stroke: var(--jp-layout-color4);
}

/* inverse recolor the accent elements of an icon */
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[fill] {
  fill: var(--jp-inverse-layout-color0);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[fill] {
  fill: var(--jp-inverse-layout-color1);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[fill] {
  fill: var(--jp-inverse-layout-color2);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[fill] {
  fill: var(--jp-inverse-layout-color3);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-IFrame {
  width: 100%;
  height: 100%;
}

.jp-IFrame > iframe {
  border: none;
}

/*
When drag events occur, `lm-mod-override-cursor` is added to the body.
Because iframes steal all cursor events, the following two rules are necessary
to suppress pointer events while resize drags are occurring. There may be a
better solution to this problem.
*/
body.lm-mod-override-cursor .jp-IFrame {
  position: relative;
}

body.lm-mod-override-cursor .jp-IFrame::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-HoverBox {
  position: fixed;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-FormGroup-content fieldset {
  border: none;
  padding: 0;
  min-width: 0;
  width: 100%;
}

/* stylelint-disable selector-max-type */

.jp-FormGroup-content fieldset .jp-inputFieldWrapper input,
.jp-FormGroup-content fieldset .jp-inputFieldWrapper select,
.jp-FormGroup-content fieldset .jp-inputFieldWrapper textarea {
  font-size: var(--jp-content-font-size2);
  border-color: var(--jp-input-border-color);
  border-style: solid;
  border-radius: var(--jp-border-radius);
  border-width: 1px;
  padding: 6px 8px;
  background: none;
  color: var(--jp-ui-font-color0);
  height: inherit;
}

.jp-FormGroup-content fieldset input[type='checkbox'] {
  position: relative;
  top: 2px;
  margin-left: 0;
}

.jp-FormGroup-content button.jp-mod-styled {
  cursor: pointer;
}

.jp-FormGroup-content .checkbox label {
  cursor: pointer;
  font-size: var(--jp-content-font-size1);
}

.jp-FormGroup-content .jp-root > fieldset > legend {
  display: none;
}

.jp-FormGroup-content .jp-root > fieldset > p {
  display: none;
}

/** copy of `input.jp-mod-styled:focus` style */
.jp-FormGroup-content fieldset input:focus,
.jp-FormGroup-content fieldset select:focus {
  -moz-outline-radius: unset;
  outline: var(--jp-border-width) solid var(--md-blue-500);
  outline-offset: -1px;
  box-shadow: inset 0 0 4px var(--md-blue-300);
}

.jp-FormGroup-content fieldset input:hover:not(:focus),
.jp-FormGroup-content fieldset select:hover:not(:focus) {
  background-color: var(--jp-border-color2);
}

/* stylelint-enable selector-max-type */

.jp-FormGroup-content .checkbox .field-description {
  /* Disable default description field for checkbox:
   because other widgets do not have description fields,
   we add descriptions to each widget on the field level.
  */
  display: none;
}

.jp-FormGroup-content #root__description {
  display: none;
}

.jp-FormGroup-content .jp-modifiedIndicator {
  width: 5px;
  background-color: var(--jp-brand-color2);
  margin-top: 0;
  margin-left: calc(var(--jp-private-settingeditor-modifier-indent) * -1);
  flex-shrink: 0;
}

.jp-FormGroup-content .jp-modifiedIndicator.jp-errorIndicator {
  background-color: var(--jp-error-color0);
  margin-right: 0.5em;
}

/* RJSF ARRAY style */

.jp-arrayFieldWrapper legend {
  font-size: var(--jp-content-font-size2);
  color: var(--jp-ui-font-color0);
  flex-basis: 100%;
  padding: 4px 0;
  font-weight: var(--jp-content-heading-font-weight);
  border-bottom: 1px solid var(--jp-border-color2);
}

.jp-arrayFieldWrapper .field-description {
  padding: 4px 0;
  white-space: pre-wrap;
}

.jp-arrayFieldWrapper .array-item {
  width: 100%;
  border: 1px solid var(--jp-border-color2);
  border-radius: 4px;
  margin: 4px;
}

.jp-ArrayOperations {
  display: flex;
  margin-left: 8px;
}

.jp-ArrayOperationsButton {
  margin: 2px;
}

.jp-ArrayOperationsButton .jp-icon3[fill] {
  fill: var(--jp-ui-font-color0);
}

button.jp-ArrayOperationsButton.jp-mod-styled:disabled {
  cursor: not-allowed;
  opacity: 0.5;
}

/* RJSF form validation error */

.jp-FormGroup-content .validationErrors {
  color: var(--jp-error-color0);
}

/* Hide panel level error as duplicated the field level error */
.jp-FormGroup-content .panel.errors {
  display: none;
}

/* RJSF normal content (settings-editor) */

.jp-FormGroup-contentNormal {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
}

.jp-FormGroup-contentNormal .jp-FormGroup-contentItem {
  margin-left: 7px;
  color: var(--jp-ui-font-color0);
}

.jp-FormGroup-contentNormal .jp-FormGroup-description {
  flex-basis: 100%;
  padding: 4px 7px;
}

.jp-FormGroup-contentNormal .jp-FormGroup-default {
  flex-basis: 100%;
  padding: 4px 7px;
}

.jp-FormGroup-contentNormal .jp-FormGroup-fieldLabel {
  font-size: var(--jp-content-font-size1);
  font-weight: normal;
  min-width: 120px;
}

.jp-FormGroup-contentNormal fieldset:not(:first-child) {
  margin-left: 7px;
}

.jp-FormGroup-contentNormal .field-array-of-string .array-item {
  /* Display `jp-ArrayOperations` buttons side-by-side with content except
    for small screens where flex-wrap will place them one below the other.
  */
  display: flex;
  align-items: center;
  flex-wrap: wrap;
}

.jp-FormGroup-contentNormal .jp-objectFieldWrapper .form-group {
  padding: 2px 8px 2px var(--jp-private-settingeditor-modifier-indent);
  margin-top: 2px;
}

/* RJSF compact content (metadata-form) */

.jp-FormGroup-content.jp-FormGroup-contentCompact {
  width: 100%;
}

.jp-FormGroup-contentCompact .form-group {
  display: flex;
  padding: 0.5em 0.2em 0.5em 0;
}

.jp-FormGroup-contentCompact
  .jp-FormGroup-compactTitle
  .jp-FormGroup-description {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color2);
}

.jp-FormGroup-contentCompact .jp-FormGroup-fieldLabel {
  padding-bottom: 0.3em;
}

.jp-FormGroup-contentCompact .jp-inputFieldWrapper .form-control {
  width: 100%;
  box-sizing: border-box;
}

.jp-FormGroup-contentCompact .jp-arrayFieldWrapper .jp-FormGroup-compactTitle {
  padding-bottom: 7px;
}

.jp-FormGroup-contentCompact
  .jp-objectFieldWrapper
  .jp-objectFieldWrapper
  .form-group {
  padding: 2px 8px 2px var(--jp-private-settingeditor-modifier-indent);
  margin-top: 2px;
}

.jp-FormGroup-contentCompact ul.error-detail {
  margin-block-start: 0.5em;
  margin-block-end: 0.5em;
  padding-inline-start: 1em;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

.jp-SidePanel {
  display: flex;
  flex-direction: column;
  min-width: var(--jp-sidebar-min-width);
  overflow-y: auto;
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  font-size: var(--jp-ui-font-size1);
}

.jp-SidePanel-header {
  flex: 0 0 auto;
  display: flex;
  border-bottom: var(--jp-border-width) solid var(--jp-border-color2);
  font-size: var(--jp-ui-font-size0);
  font-weight: 600;
  letter-spacing: 1px;
  margin: 0;
  padding: 2px;
  text-transform: uppercase;
}

.jp-SidePanel-toolbar {
  flex: 0 0 auto;
}

.jp-SidePanel-content {
  flex: 1 1 auto;
}

.jp-SidePanel-toolbar,
.jp-AccordionPanel-toolbar {
  height: var(--jp-private-toolbar-height);
}

.jp-SidePanel-toolbar.jp-Toolbar-micro {
  display: none;
}

.lm-AccordionPanel .jp-AccordionPanel-title {
  box-sizing: border-box;
  line-height: 25px;
  margin: 0;
  display: flex;
  align-items: center;
  background: var(--jp-layout-color1);
  color: var(--jp-ui-font-color1);
  border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  box-shadow: var(--jp-toolbar-box-shadow);
  font-size: var(--jp-ui-font-size0);
}

.jp-AccordionPanel-title {
  cursor: pointer;
  user-select: none;
  -moz-user-select: none;
  -webkit-user-select: none;
  text-transform: uppercase;
}

.lm-AccordionPanel[data-orientation='horizontal'] > .jp-AccordionPanel-title {
  /* Title is rotated for horizontal accordion panel using CSS */
  display: block;
  transform-origin: top left;
  transform: rotate(-90deg) translate(-100%);
}

.jp-AccordionPanel-title .lm-AccordionPanel-titleLabel {
  user-select: none;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}

.jp-AccordionPanel-title .lm-AccordionPanel-titleCollapser {
  transform: rotate(-90deg);
  margin: auto 0;
  height: 16px;
}

.jp-AccordionPanel-title.lm-mod-expanded .lm-AccordionPanel-titleCollapser {
  transform: rotate(0deg);
}

.lm-AccordionPanel .jp-AccordionPanel-toolbar {
  background: none;
  box-shadow: none;
  border: none;
  margin-left: auto;
}

.lm-AccordionPanel .lm-SplitPanel-handle:hover {
  background: var(--jp-layout-color3);
}

.jp-text-truncated {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Spinner {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 10;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: var(--jp-layout-color0);
  outline: none;
}

.jp-SpinnerContent {
  font-size: 10px;
  margin: 50px auto;
  text-indent: -9999em;
  width: 3em;
  height: 3em;
  border-radius: 50%;
  background: var(--jp-brand-color3);
  background: linear-gradient(
    to right,
    #f37626 10%,
    rgba(255, 255, 255, 0) 42%
  );
  position: relative;
  animation: load3 1s infinite linear, fadeIn 1s;
}

.jp-SpinnerContent::before {
  width: 50%;
  height: 50%;
  background: #f37626;
  border-radius: 100% 0 0;
  position: absolute;
  top: 0;
  left: 0;
  content: '';
}

.jp-SpinnerContent::after {
  background: var(--jp-layout-color0);
  width: 75%;
  height: 75%;
  border-radius: 50%;
  content: '';
  margin: auto;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }

  100% {
    opacity: 1;
  }
}

@keyframes load3 {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

button.jp-mod-styled {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  border: none;
  box-sizing: border-box;
  text-align: center;
  line-height: 32px;
  height: 32px;
  padding: 0 12px;
  letter-spacing: 0.8px;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

input.jp-mod-styled {
  background: var(--jp-input-background);
  height: 28px;
  box-sizing: border-box;
  border: var(--jp-border-width) solid var(--jp-border-color1);
  padding-left: 7px;
  padding-right: 7px;
  font-size: var(--jp-ui-font-size2);
  color: var(--jp-ui-font-color0);
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

input[type='checkbox'].jp-mod-styled {
  appearance: checkbox;
  -webkit-appearance: checkbox;
  -moz-appearance: checkbox;
  height: auto;
}

input.jp-mod-styled:focus {
  border: var(--jp-border-width) solid var(--md-blue-500);
  box-shadow: inset 0 0 4px var(--md-blue-300);
}

.jp-select-wrapper {
  display: flex;
  position: relative;
  flex-direction: column;
  padding: 1px;
  background-color: var(--jp-layout-color1);
  box-sizing: border-box;
  margin-bottom: 12px;
}

.jp-select-wrapper:not(.multiple) {
  height: 28px;
}

.jp-select-wrapper.jp-mod-focused select.jp-mod-styled {
  border: var(--jp-border-width) solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
  background-color: var(--jp-input-active-background);
}

select.jp-mod-styled:hover {
  cursor: pointer;
  color: var(--jp-ui-font-color0);
  background-color: var(--jp-input-hover-background);
  box-shadow: inset 0 0 1px rgba(0, 0, 0, 0.5);
}

select.jp-mod-styled {
  flex: 1 1 auto;
  width: 100%;
  font-size: var(--jp-ui-font-size2);
  background: var(--jp-input-background);
  color: var(--jp-ui-font-color0);
  padding: 0 25px 0 8px;
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  border-radius: 0;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

select.jp-mod-styled:not([multiple]) {
  height: 32px;
}

select.jp-mod-styled[multiple] {
  max-height: 200px;
  overflow-y: auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-switch {
  display: flex;
  align-items: center;
  padding-left: 4px;
  padding-right: 4px;
  font-size: var(--jp-ui-font-size1);
  background-color: transparent;
  color: var(--jp-ui-font-color1);
  border: none;
  height: 20px;
}

.jp-switch:hover {
  background-color: var(--jp-layout-color2);
}

.jp-switch-label {
  margin-right: 5px;
  font-family: var(--jp-ui-font-family);
}

.jp-switch-track {
  cursor: pointer;
  background-color: var(--jp-switch-color, var(--jp-border-color1));
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 34px;
  height: 16px;
  width: 35px;
  position: relative;
}

.jp-switch-track::before {
  content: '';
  position: absolute;
  height: 10px;
  width: 10px;
  margin: 3px;
  left: 0;
  background-color: var(--jp-ui-inverse-font-color1);
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 50%;
}

.jp-switch[aria-checked='true'] .jp-switch-track {
  background-color: var(--jp-switch-true-position-color, var(--jp-warn-color0));
}

.jp-switch[aria-checked='true'] .jp-switch-track::before {
  /* track width (35) - margins (3 + 3) - thumb width (10) */
  left: 19px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

:root {
  --jp-private-toolbar-height: calc(
    28px + var(--jp-border-width)
  ); /* leave 28px for content */
}

.jp-Toolbar {
  color: var(--jp-ui-font-color1);
  flex: 0 0 auto;
  display: flex;
  flex-direction: row;
  border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  box-shadow: var(--jp-toolbar-box-shadow);
  background: var(--jp-toolbar-background);
  min-height: var(--jp-toolbar-micro-height);
  padding: 2px;
  z-index: 8;
  overflow-x: hidden;
}

/* Toolbar items */

.jp-Toolbar > .jp-Toolbar-item.jp-Toolbar-spacer {
  flex-grow: 1;
  flex-shrink: 1;
}

.jp-Toolbar-item.jp-Toolbar-kernelStatus {
  display: inline-block;
  width: 32px;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 16px;
}

.jp-Toolbar > .jp-Toolbar-item {
  flex: 0 0 auto;
  display: flex;
  padding-left: 1px;
  padding-right: 1px;
  font-size: var(--jp-ui-font-size1);
  line-height: var(--jp-private-toolbar-height);
  height: 100%;
}

/* Toolbar buttons */

/* This is the div we use to wrap the react component into a Widget */
div.jp-ToolbarButton {
  color: transparent;
  border: none;
  box-sizing: border-box;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 0;
  margin: 0;
}

button.jp-ToolbarButtonComponent {
  background: var(--jp-layout-color1);
  border: none;
  box-sizing: border-box;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 0 6px;
  margin: 0;
  height: 24px;
  border-radius: var(--jp-border-radius);
  display: flex;
  align-items: center;
  text-align: center;
  font-size: 14px;
  min-width: unset;
  min-height: unset;
}

button.jp-ToolbarButtonComponent:disabled {
  opacity: 0.4;
}

button.jp-ToolbarButtonComponent > span {
  padding: 0;
  flex: 0 0 auto;
}

button.jp-ToolbarButtonComponent .jp-ToolbarButtonComponent-label {
  font-size: var(--jp-ui-font-size1);
  line-height: 100%;
  padding-left: 2px;
  color: var(--jp-ui-font-color1);
  font-family: var(--jp-ui-font-family);
}

#jp-main-dock-panel[data-mode='single-document']
  .jp-MainAreaWidget
  > .jp-Toolbar.jp-Toolbar-micro {
  padding: 0;
  min-height: 0;
}

#jp-main-dock-panel[data-mode='single-document']
  .jp-MainAreaWidget
  > .jp-Toolbar {
  border: none;
  box-shadow: none;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

.jp-WindowedPanel-outer {
  position: relative;
  overflow-y: auto;
}

.jp-WindowedPanel-inner {
  position: relative;
}

.jp-WindowedPanel-window {
  position: absolute;
  left: 0;
  right: 0;
  overflow: visible;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* Sibling imports */

body {
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
}

/* Disable native link decoration styles everywhere outside of dialog boxes */
a {
  text-decoration: unset;
  color: unset;
}

a:hover {
  text-decoration: unset;
  color: unset;
}

/* Accessibility for links inside dialog box text */
.jp-Dialog-content a {
  text-decoration: revert;
  color: var(--jp-content-link-color);
}

.jp-Dialog-content a:hover {
  text-decoration: revert;
}

/* Styles for ui-components */
.jp-Button {
  color: var(--jp-ui-font-color2);
  border-radius: var(--jp-border-radius);
  padding: 0 12px;
  font-size: var(--jp-ui-font-size1);

  /* Copy from blueprint 3 */
  display: inline-flex;
  flex-direction: row;
  border: none;
  cursor: pointer;
  align-items: center;
  justify-content: center;
  text-align: left;
  vertical-align: middle;
  min-height: 30px;
  min-width: 30px;
}

.jp-Button:disabled {
  cursor: not-allowed;
}

.jp-Button:empty {
  padding: 0 !important;
}

.jp-Button.jp-mod-small {
  min-height: 24px;
  min-width: 24px;
  font-size: 12px;
  padding: 0 7px;
}

/* Use our own theme for hover styles */
.jp-Button.jp-mod-minimal:hover {
  background-color: var(--jp-layout-color2);
}

.jp-Button.jp-mod-minimal {
  background: none;
}

.jp-InputGroup {
  display: block;
  position: relative;
}

.jp-InputGroup input {
  box-sizing: border-box;
  border: none;
  border-radius: 0;
  background-color: transparent;
  color: var(--jp-ui-font-color0);
  box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
  padding-bottom: 0;
  padding-top: 0;
  padding-left: 10px;
  padding-right: 28px;
  position: relative;
  width: 100%;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  font-size: 14px;
  font-weight: 400;
  height: 30px;
  line-height: 30px;
  outline: none;
  vertical-align: middle;
}

.jp-InputGroup input:focus {
  box-shadow: inset 0 0 0 var(--jp-border-width)
      var(--jp-input-active-box-shadow-color),
    inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
}

.jp-InputGroup input:disabled {
  cursor: not-allowed;
  resize: block;
  background-color: var(--jp-layout-color2);
  color: var(--jp-ui-font-color2);
}

.jp-InputGroup input:disabled ~ span {
  cursor: not-allowed;
  color: var(--jp-ui-font-color2);
}

.jp-InputGroup input::placeholder,
input::placeholder {
  color: var(--jp-ui-font-color2);
}

.jp-InputGroupAction {
  position: absolute;
  bottom: 1px;
  right: 0;
  padding: 6px;
}

.jp-HTMLSelect.jp-DefaultStyle select {
  background-color: initial;
  border: none;
  border-radius: 0;
  box-shadow: none;
  color: var(--jp-ui-font-color0);
  display: block;
  font-size: var(--jp-ui-font-size1);
  font-family: var(--jp-ui-font-family);
  height: 24px;
  line-height: 14px;
  padding: 0 25px 0 10px;
  text-align: left;
  -moz-appearance: none;
  -webkit-appearance: none;
}

.jp-HTMLSelect.jp-DefaultStyle select:disabled {
  background-color: var(--jp-layout-color2);
  color: var(--jp-ui-font-color2);
  cursor: not-allowed;
  resize: block;
}

.jp-HTMLSelect.jp-DefaultStyle select:disabled ~ span {
  cursor: not-allowed;
}

/* Use our own theme for hover and option styles */
/* stylelint-disable-next-line selector-max-type */
.jp-HTMLSelect.jp-DefaultStyle select:hover,
.jp-HTMLSelect.jp-DefaultStyle select > option {
  background-color: var(--jp-layout-color2);
  color: var(--jp-ui-font-color0);
}

select {
  box-sizing: border-box;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Styles
|----------------------------------------------------------------------------*/

.jp-StatusBar-Widget {
  display: flex;
  align-items: center;
  background: var(--jp-layout-color2);
  min-height: var(--jp-statusbar-height);
  justify-content: space-between;
  padding: 0 10px;
}

.jp-StatusBar-Left {
  display: flex;
  align-items: center;
  flex-direction: row;
}

.jp-StatusBar-Middle {
  display: flex;
  align-items: center;
}

.jp-StatusBar-Right {
  display: flex;
  align-items: center;
  flex-direction: row-reverse;
}

.jp-StatusBar-Item {
  max-height: var(--jp-statusbar-height);
  margin: 0 2px;
  height: var(--jp-statusbar-height);
  white-space: nowrap;
  text-overflow: ellipsis;
  color: var(--jp-ui-font-color1);
  padding: 0 6px;
}

.jp-mod-highlighted:hover {
  background-color: var(--jp-layout-color3);
}

.jp-mod-clicked {
  background-color: var(--jp-brand-color1);
}

.jp-mod-clicked:hover {
  background-color: var(--jp-brand-color0);
}

.jp-mod-clicked .jp-StatusBar-TextItem {
  color: var(--jp-ui-inverse-font-color1);
}

.jp-StatusBar-HoverItem {
  box-shadow: '0px 4px 4px rgba(0, 0, 0, 0.25)';
}

.jp-StatusBar-TextItem {
  font-size: var(--jp-ui-font-size1);
  font-family: var(--jp-ui-font-family);
  line-height: 24px;
  color: var(--jp-ui-font-color1);
}

.jp-StatusBar-GroupItem {
  display: flex;
  align-items: center;
  flex-direction: row;
}

.jp-Statusbar-ProgressCircle svg {
  display: block;
  margin: 0 auto;
  width: 16px;
  height: 24px;
  align-self: normal;
}

.jp-Statusbar-ProgressCircle path {
  fill: var(--jp-inverse-layout-color3);
}

.jp-Statusbar-ProgressBar-progress-bar {
  height: 10px;
  width: 100px;
  border: solid 0.25px var(--jp-brand-color2);
  border-radius: 3px;
  overflow: hidden;
  align-self: center;
}

.jp-Statusbar-ProgressBar-progress-bar > div {
  background-color: var(--jp-brand-color2);
  background-image: linear-gradient(
    -45deg,
    rgba(255, 255, 255, 0.2) 25%,
    transparent 25%,
    transparent 50%,
    rgba(255, 255, 255, 0.2) 50%,
    rgba(255, 255, 255, 0.2) 75%,
    transparent 75%,
    transparent
  );
  background-size: 40px 40px;
  float: left;
  width: 0%;
  height: 100%;
  font-size: 12px;
  line-height: 14px;
  color: #fff;
  text-align: center;
  animation: jp-Statusbar-ExecutionTime-progress-bar 2s linear infinite;
}

.jp-Statusbar-ProgressBar-progress-bar p {
  color: var(--jp-ui-font-color1);
  font-family: var(--jp-ui-font-family);
  font-size: var(--jp-ui-font-size1);
  line-height: 10px;
  width: 100px;
}

@keyframes jp-Statusbar-ExecutionTime-progress-bar {
  0% {
    background-position: 0 0;
  }

  100% {
    background-position: 40px 40px;
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-commandpalette-search-height: 28px;
}

/*-----------------------------------------------------------------------------
| Overall styles
|----------------------------------------------------------------------------*/

.lm-CommandPalette {
  padding-bottom: 0;
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);

  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
}

/*-----------------------------------------------------------------------------
| Modal variant
|----------------------------------------------------------------------------*/

.jp-ModalCommandPalette {
  position: absolute;
  z-index: 10000;
  top: 38px;
  left: 30%;
  margin: 0;
  padding: 4px;
  width: 40%;
  box-shadow: var(--jp-elevation-z4);
  border-radius: 4px;
  background: var(--jp-layout-color0);
}

.jp-ModalCommandPalette .lm-CommandPalette {
  max-height: 40vh;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-close-icon::after {
  display: none;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-header {
  display: none;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-item {
  margin-left: 4px;
  margin-right: 4px;
}

.jp-ModalCommandPalette
  .lm-CommandPalette
  .lm-CommandPalette-item.lm-mod-disabled {
  display: none;
}

/*-----------------------------------------------------------------------------
| Search
|----------------------------------------------------------------------------*/

.lm-CommandPalette-search {
  padding: 4px;
  background-color: var(--jp-layout-color1);
  z-index: 2;
}

.lm-CommandPalette-wrapper {
  overflow: overlay;
  padding: 0 9px;
  background-color: var(--jp-input-active-background);
  height: 30px;
  box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
}

.lm-CommandPalette.lm-mod-focused .lm-CommandPalette-wrapper {
  box-shadow: inset 0 0 0 1px var(--jp-input-active-box-shadow-color),
    inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
}

.jp-SearchIconGroup {
  color: white;
  background-color: var(--jp-brand-color1);
  position: absolute;
  top: 4px;
  right: 4px;
  padding: 5px 5px 1px;
}

.jp-SearchIconGroup svg {
  height: 20px;
  width: 20px;
}

.jp-SearchIconGroup .jp-icon3[fill] {
  fill: var(--jp-layout-color0);
}

.lm-CommandPalette-input {
  background: transparent;
  width: calc(100% - 18px);
  float: left;
  border: none;
  outline: none;
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  line-height: var(--jp-private-commandpalette-search-height);
}

.lm-CommandPalette-input::-webkit-input-placeholder,
.lm-CommandPalette-input::-moz-placeholder,
.lm-CommandPalette-input:-ms-input-placeholder {
  color: var(--jp-ui-font-color2);
  font-size: var(--jp-ui-font-size1);
}

/*-----------------------------------------------------------------------------
| Results
|----------------------------------------------------------------------------*/

.lm-CommandPalette-header:first-child {
  margin-top: 0;
}

.lm-CommandPalette-header {
  border-bottom: solid var(--jp-border-width) var(--jp-border-color2);
  color: var(--jp-ui-font-color1);
  cursor: pointer;
  display: flex;
  font-size: var(--jp-ui-font-size0);
  font-weight: 600;
  letter-spacing: 1px;
  margin-top: 8px;
  padding: 8px 0 8px 12px;
  text-transform: uppercase;
}

.lm-CommandPalette-header.lm-mod-active {
  background: var(--jp-layout-color2);
}

.lm-CommandPalette-header > mark {
  background-color: transparent;
  font-weight: bold;
  color: var(--jp-ui-font-color1);
}

.lm-CommandPalette-item {
  padding: 4px 12px 4px 4px;
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
  font-weight: 400;
  display: flex;
}

.lm-CommandPalette-item.lm-mod-disabled {
  color: var(--jp-ui-font-color2);
}

.lm-CommandPalette-item.lm-mod-active {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.lm-CommandPalette-item.lm-mod-active .lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-inverse-font-color0);
}

.lm-CommandPalette-item.lm-mod-active .jp-icon-selectable[fill] {
  fill: var(--jp-layout-color0);
}

.lm-CommandPalette-item.lm-mod-active:hover:not(.lm-mod-disabled) {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.lm-CommandPalette-item:hover:not(.lm-mod-active):not(.lm-mod-disabled) {
  background: var(--jp-layout-color2);
}

.lm-CommandPalette-itemContent {
  overflow: hidden;
}

.lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-font-color0);
  background-color: transparent;
  font-weight: bold;
}

.lm-CommandPalette-item.lm-mod-disabled mark {
  color: var(--jp-ui-font-color2);
}

.lm-CommandPalette-item .lm-CommandPalette-itemIcon {
  margin: 0 4px 0 0;
  position: relative;
  width: 16px;
  top: 2px;
  flex: 0 0 auto;
}

.lm-CommandPalette-item.lm-mod-disabled .lm-CommandPalette-itemIcon {
  opacity: 0.6;
}

.lm-CommandPalette-item .lm-CommandPalette-itemShortcut {
  flex: 0 0 auto;
}

.lm-CommandPalette-itemCaption {
  display: none;
}

.lm-CommandPalette-content {
  background-color: var(--jp-layout-color1);
}

.lm-CommandPalette-content:empty::after {
  content: 'No results';
  margin: auto;
  margin-top: 20px;
  width: 100px;
  display: block;
  font-size: var(--jp-ui-font-size2);
  font-family: var(--jp-ui-font-family);
  font-weight: lighter;
}

.lm-CommandPalette-emptyMessage {
  text-align: center;
  margin-top: 24px;
  line-height: 1.32;
  padding: 0 8px;
  color: var(--jp-content-font-color3);
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Dialog {
  position: absolute;
  z-index: 10000;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  top: 0;
  left: 0;
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background: var(--jp-dialog-background);
}

.jp-Dialog-content {
  display: flex;
  flex-direction: column;
  margin-left: auto;
  margin-right: auto;
  background: var(--jp-layout-color1);
  padding: 24px 24px 12px;
  min-width: 300px;
  min-height: 150px;
  max-width: 1000px;
  max-height: 500px;
  box-sizing: border-box;
  box-shadow: var(--jp-elevation-z20);
  word-wrap: break-word;
  border-radius: var(--jp-border-radius);

  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color1);
  resize: both;
}

.jp-Dialog-content.jp-Dialog-content-small {
  max-width: 500px;
}

.jp-Dialog-button {
  overflow: visible;
}

button.jp-Dialog-button:focus {
  outline: 1px solid var(--jp-brand-color1);
  outline-offset: 4px;
  -moz-outline-radius: 0;
}

button.jp-Dialog-button:focus::-moz-focus-inner {
  border: 0;
}

button.jp-Dialog-button.jp-mod-styled.jp-mod-accept:focus,
button.jp-Dialog-button.jp-mod-styled.jp-mod-warn:focus,
button.jp-Dialog-button.jp-mod-styled.jp-mod-reject:focus {
  outline-offset: 4px;
  -moz-outline-radius: 0;
}

button.jp-Dialog-button.jp-mod-styled.jp-mod-accept:focus {
  outline: 1px solid var(--jp-accept-color-normal, var(--jp-brand-color1));
}

button.jp-Dialog-button.jp-mod-styled.jp-mod-warn:focus {
  outline: 1px solid var(--jp-warn-color-normal, var(--jp-error-color1));
}

button.jp-Dialog-button.jp-mod-styled.jp-mod-reject:focus {
  outline: 1px solid var(--jp-reject-color-normal, var(--md-grey-600));
}

button.jp-Dialog-close-button {
  padding: 0;
  height: 100%;
  min-width: unset;
  min-height: unset;
}

.jp-Dialog-header {
  display: flex;
  justify-content: space-between;
  flex: 0 0 auto;
  padding-bottom: 12px;
  font-size: var(--jp-ui-font-size3);
  font-weight: 400;
  color: var(--jp-ui-font-color1);
}

.jp-Dialog-body {
  display: flex;
  flex-direction: column;
  flex: 1 1 auto;
  font-size: var(--jp-ui-font-size1);
  background: var(--jp-layout-color1);
  color: var(--jp-ui-font-color1);
  overflow: auto;
}

.jp-Dialog-footer {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  align-items: center;
  flex: 0 0 auto;
  margin-left: -12px;
  margin-right: -12px;
  padding: 12px;
}

.jp-Dialog-checkbox {
  padding-right: 5px;
}

.jp-Dialog-checkbox > input:focus-visible {
  outline: 1px solid var(--jp-input-active-border-color);
  outline-offset: 1px;
}

.jp-Dialog-spacer {
  flex: 1 1 auto;
}

.jp-Dialog-title {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.jp-Dialog-body > .jp-select-wrapper {
  width: 100%;
}

.jp-Dialog-body > button {
  padding: 0 16px;
}

.jp-Dialog-body > label {
  line-height: 1.4;
  color: var(--jp-ui-font-color0);
}

.jp-Dialog-button.jp-mod-styled:not(:last-child) {
  margin-right: 12px;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

.jp-Input-Boolean-Dialog {
  flex-direction: row-reverse;
  align-items: end;
  width: 100%;
}

.jp-Input-Boolean-Dialog > label {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-MainAreaWidget > :focus {
  outline: none;
}

.jp-MainAreaWidget .jp-MainAreaWidget-error {
  padding: 6px;
}

.jp-MainAreaWidget .jp-MainAreaWidget-error > pre {
  width: auto;
  padding: 10px;
  background: var(--jp-error-color3);
  border: var(--jp-border-width) solid var(--jp-error-color1);
  border-radius: var(--jp-border-radius);
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
  white-space: pre-wrap;
  word-wrap: break-word;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/**
 * google-material-color v1.2.6
 * https://github.com/danlevan/google-material-color
 */
:root {
  --md-red-50: #ffebee;
  --md-red-100: #ffcdd2;
  --md-red-200: #ef9a9a;
  --md-red-300: #e57373;
  --md-red-400: #ef5350;
  --md-red-500: #f44336;
  --md-red-600: #e53935;
  --md-red-700: #d32f2f;
  --md-red-800: #c62828;
  --md-red-900: #b71c1c;
  --md-red-A100: #ff8a80;
  --md-red-A200: #ff5252;
  --md-red-A400: #ff1744;
  --md-red-A700: #d50000;
  --md-pink-50: #fce4ec;
  --md-pink-100: #f8bbd0;
  --md-pink-200: #f48fb1;
  --md-pink-300: #f06292;
  --md-pink-400: #ec407a;
  --md-pink-500: #e91e63;
  --md-pink-600: #d81b60;
  --md-pink-700: #c2185b;
  --md-pink-800: #ad1457;
  --md-pink-900: #880e4f;
  --md-pink-A100: #ff80ab;
  --md-pink-A200: #ff4081;
  --md-pink-A400: #f50057;
  --md-pink-A700: #c51162;
  --md-purple-50: #f3e5f5;
  --md-purple-100: #e1bee7;
  --md-purple-200: #ce93d8;
  --md-purple-300: #ba68c8;
  --md-purple-400: #ab47bc;
  --md-purple-500: #9c27b0;
  --md-purple-600: #8e24aa;
  --md-purple-700: #7b1fa2;
  --md-purple-800: #6a1b9a;
  --md-purple-900: #4a148c;
  --md-purple-A100: #ea80fc;
  --md-purple-A200: #e040fb;
  --md-purple-A400: #d500f9;
  --md-purple-A700: #a0f;
  --md-deep-purple-50: #ede7f6;
  --md-deep-purple-100: #d1c4e9;
  --md-deep-purple-200: #b39ddb;
  --md-deep-purple-300: #9575cd;
  --md-deep-purple-400: #7e57c2;
  --md-deep-purple-500: #673ab7;
  --md-deep-purple-600: #5e35b1;
  --md-deep-purple-700: #512da8;
  --md-deep-purple-800: #4527a0;
  --md-deep-purple-900: #311b92;
  --md-deep-purple-A100: #b388ff;
  --md-deep-purple-A200: #7c4dff;
  --md-deep-purple-A400: #651fff;
  --md-deep-purple-A700: #6200ea;
  --md-indigo-50: #e8eaf6;
  --md-indigo-100: #c5cae9;
  --md-indigo-200: #9fa8da;
  --md-indigo-300: #7986cb;
  --md-indigo-400: #5c6bc0;
  --md-indigo-500: #3f51b5;
  --md-indigo-600: #3949ab;
  --md-indigo-700: #303f9f;
  --md-indigo-800: #283593;
  --md-indigo-900: #1a237e;
  --md-indigo-A100: #8c9eff;
  --md-indigo-A200: #536dfe;
  --md-indigo-A400: #3d5afe;
  --md-indigo-A700: #304ffe;
  --md-blue-50: #e3f2fd;
  --md-blue-100: #bbdefb;
  --md-blue-200: #90caf9;
  --md-blue-300: #64b5f6;
  --md-blue-400: #42a5f5;
  --md-blue-500: #2196f3;
  --md-blue-600: #1e88e5;
  --md-blue-700: #1976d2;
  --md-blue-800: #1565c0;
  --md-blue-900: #0d47a1;
  --md-blue-A100: #82b1ff;
  --md-blue-A200: #448aff;
  --md-blue-A400: #2979ff;
  --md-blue-A700: #2962ff;
  --md-light-blue-50: #e1f5fe;
  --md-light-blue-100: #b3e5fc;
  --md-light-blue-200: #81d4fa;
  --md-light-blue-300: #4fc3f7;
  --md-light-blue-400: #29b6f6;
  --md-light-blue-500: #03a9f4;
  --md-light-blue-600: #039be5;
  --md-light-blue-700: #0288d1;
  --md-light-blue-800: #0277bd;
  --md-light-blue-900: #01579b;
  --md-light-blue-A100: #80d8ff;
  --md-light-blue-A200: #40c4ff;
  --md-light-blue-A400: #00b0ff;
  --md-light-blue-A700: #0091ea;
  --md-cyan-50: #e0f7fa;
  --md-cyan-100: #b2ebf2;
  --md-cyan-200: #80deea;
  --md-cyan-300: #4dd0e1;
  --md-cyan-400: #26c6da;
  --md-cyan-500: #00bcd4;
  --md-cyan-600: #00acc1;
  --md-cyan-700: #0097a7;
  --md-cyan-800: #00838f;
  --md-cyan-900: #006064;
  --md-cyan-A100: #84ffff;
  --md-cyan-A200: #18ffff;
  --md-cyan-A400: #00e5ff;
  --md-cyan-A700: #00b8d4;
  --md-teal-50: #e0f2f1;
  --md-teal-100: #b2dfdb;
  --md-teal-200: #80cbc4;
  --md-teal-300: #4db6ac;
  --md-teal-400: #26a69a;
  --md-teal-500: #009688;
  --md-teal-600: #00897b;
  --md-teal-700: #00796b;
  --md-teal-800: #00695c;
  --md-teal-900: #004d40;
  --md-teal-A100: #a7ffeb;
  --md-teal-A200: #64ffda;
  --md-teal-A400: #1de9b6;
  --md-teal-A700: #00bfa5;
  --md-green-50: #e8f5e9;
  --md-green-100: #c8e6c9;
  --md-green-200: #a5d6a7;
  --md-green-300: #81c784;
  --md-green-400: #66bb6a;
  --md-green-500: #4caf50;
  --md-green-600: #43a047;
  --md-green-700: #388e3c;
  --md-green-800: #2e7d32;
  --md-green-900: #1b5e20;
  --md-green-A100: #b9f6ca;
  --md-green-A200: #69f0ae;
  --md-green-A400: #00e676;
  --md-green-A700: #00c853;
  --md-light-green-50: #f1f8e9;
  --md-light-green-100: #dcedc8;
  --md-light-green-200: #c5e1a5;
  --md-light-green-300: #aed581;
  --md-light-green-400: #9ccc65;
  --md-light-green-500: #8bc34a;
  --md-light-green-600: #7cb342;
  --md-light-green-700: #689f38;
  --md-light-green-800: #558b2f;
  --md-light-green-900: #33691e;
  --md-light-green-A100: #ccff90;
  --md-light-green-A200: #b2ff59;
  --md-light-green-A400: #76ff03;
  --md-light-green-A700: #64dd17;
  --md-lime-50: #f9fbe7;
  --md-lime-100: #f0f4c3;
  --md-lime-200: #e6ee9c;
  --md-lime-300: #dce775;
  --md-lime-400: #d4e157;
  --md-lime-500: #cddc39;
  --md-lime-600: #c0ca33;
  --md-lime-700: #afb42b;
  --md-lime-800: #9e9d24;
  --md-lime-900: #827717;
  --md-lime-A100: #f4ff81;
  --md-lime-A200: #eeff41;
  --md-lime-A400: #c6ff00;
  --md-lime-A700: #aeea00;
  --md-yellow-50: #fffde7;
  --md-yellow-100: #fff9c4;
  --md-yellow-200: #fff59d;
  --md-yellow-300: #fff176;
  --md-yellow-400: #ffee58;
  --md-yellow-500: #ffeb3b;
  --md-yellow-600: #fdd835;
  --md-yellow-700: #fbc02d;
  --md-yellow-800: #f9a825;
  --md-yellow-900: #f57f17;
  --md-yellow-A100: #ffff8d;
  --md-yellow-A200: #ff0;
  --md-yellow-A400: #ffea00;
  --md-yellow-A700: #ffd600;
  --md-amber-50: #fff8e1;
  --md-amber-100: #ffecb3;
  --md-amber-200: #ffe082;
  --md-amber-300: #ffd54f;
  --md-amber-400: #ffca28;
  --md-amber-500: #ffc107;
  --md-amber-600: #ffb300;
  --md-amber-700: #ffa000;
  --md-amber-800: #ff8f00;
  --md-amber-900: #ff6f00;
  --md-amber-A100: #ffe57f;
  --md-amber-A200: #ffd740;
  --md-amber-A400: #ffc400;
  --md-amber-A700: #ffab00;
  --md-orange-50: #fff3e0;
  --md-orange-100: #ffe0b2;
  --md-orange-200: #ffcc80;
  --md-orange-300: #ffb74d;
  --md-orange-400: #ffa726;
  --md-orange-500: #ff9800;
  --md-orange-600: #fb8c00;
  --md-orange-700: #f57c00;
  --md-orange-800: #ef6c00;
  --md-orange-900: #e65100;
  --md-orange-A100: #ffd180;
  --md-orange-A200: #ffab40;
  --md-orange-A400: #ff9100;
  --md-orange-A700: #ff6d00;
  --md-deep-orange-50: #fbe9e7;
  --md-deep-orange-100: #ffccbc;
  --md-deep-orange-200: #ffab91;
  --md-deep-orange-300: #ff8a65;
  --md-deep-orange-400: #ff7043;
  --md-deep-orange-500: #ff5722;
  --md-deep-orange-600: #f4511e;
  --md-deep-orange-700: #e64a19;
  --md-deep-orange-800: #d84315;
  --md-deep-orange-900: #bf360c;
  --md-deep-orange-A100: #ff9e80;
  --md-deep-orange-A200: #ff6e40;
  --md-deep-orange-A400: #ff3d00;
  --md-deep-orange-A700: #dd2c00;
  --md-brown-50: #efebe9;
  --md-brown-100: #d7ccc8;
  --md-brown-200: #bcaaa4;
  --md-brown-300: #a1887f;
  --md-brown-400: #8d6e63;
  --md-brown-500: #795548;
  --md-brown-600: #6d4c41;
  --md-brown-700: #5d4037;
  --md-brown-800: #4e342e;
  --md-brown-900: #3e2723;
  --md-grey-50: #fafafa;
  --md-grey-100: #f5f5f5;
  --md-grey-200: #eee;
  --md-grey-300: #e0e0e0;
  --md-grey-400: #bdbdbd;
  --md-grey-500: #9e9e9e;
  --md-grey-600: #757575;
  --md-grey-700: #616161;
  --md-grey-800: #424242;
  --md-grey-900: #212121;
  --md-blue-grey-50: #eceff1;
  --md-blue-grey-100: #cfd8dc;
  --md-blue-grey-200: #b0bec5;
  --md-blue-grey-300: #90a4ae;
  --md-blue-grey-400: #78909c;
  --md-blue-grey-500: #607d8b;
  --md-blue-grey-600: #546e7a;
  --md-blue-grey-700: #455a64;
  --md-blue-grey-800: #37474f;
  --md-blue-grey-900: #263238;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| RenderedText
|----------------------------------------------------------------------------*/

:root {
  /* This is the padding value to fill the gaps between lines containing spans with background color. */
  --jp-private-code-span-padding: calc(
    (var(--jp-code-line-height) - 1) * var(--jp-code-font-size) / 2
  );
}

.jp-RenderedText {
  text-align: left;
  padding-left: var(--jp-code-padding);
  line-height: var(--jp-code-line-height);
  font-family: var(--jp-code-font-family);
}

.jp-RenderedText pre,
.jp-RenderedJavaScript pre,
.jp-RenderedHTMLCommon pre {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-code-font-size);
  border: none;
  margin: 0;
  padding: 0;
}

.jp-RenderedText pre a:link {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

.jp-RenderedText pre a:hover {
  text-decoration: underline;
  color: var(--jp-content-link-color);
}

.jp-RenderedText pre a:visited {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

/* console foregrounds and backgrounds */
.jp-RenderedText pre .ansi-black-fg {
  color: #3e424d;
}

.jp-RenderedText pre .ansi-red-fg {
  color: #e75c58;
}

.jp-RenderedText pre .ansi-green-fg {
  color: #00a250;
}

.jp-RenderedText pre .ansi-yellow-fg {
  color: #ddb62b;
}

.jp-RenderedText pre .ansi-blue-fg {
  color: #208ffb;
}

.jp-RenderedText pre .ansi-magenta-fg {
  color: #d160c4;
}

.jp-RenderedText pre .ansi-cyan-fg {
  color: #60c6c8;
}

.jp-RenderedText pre .ansi-white-fg {
  color: #c5c1b4;
}

.jp-RenderedText pre .ansi-black-bg {
  background-color: #3e424d;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-red-bg {
  background-color: #e75c58;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-green-bg {
  background-color: #00a250;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-yellow-bg {
  background-color: #ddb62b;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-blue-bg {
  background-color: #208ffb;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-magenta-bg {
  background-color: #d160c4;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-cyan-bg {
  background-color: #60c6c8;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-white-bg {
  background-color: #c5c1b4;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-black-intense-fg {
  color: #282c36;
}

.jp-RenderedText pre .ansi-red-intense-fg {
  color: #b22b31;
}

.jp-RenderedText pre .ansi-green-intense-fg {
  color: #007427;
}

.jp-RenderedText pre .ansi-yellow-intense-fg {
  color: #b27d12;
}

.jp-RenderedText pre .ansi-blue-intense-fg {
  color: #0065ca;
}

.jp-RenderedText pre .ansi-magenta-intense-fg {
  color: #a03196;
}

.jp-RenderedText pre .ansi-cyan-intense-fg {
  color: #258f8f;
}

.jp-RenderedText pre .ansi-white-intense-fg {
  color: #a1a6b2;
}

.jp-RenderedText pre .ansi-black-intense-bg {
  background-color: #282c36;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-red-intense-bg {
  background-color: #b22b31;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-green-intense-bg {
  background-color: #007427;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-yellow-intense-bg {
  background-color: #b27d12;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-blue-intense-bg {
  background-color: #0065ca;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-magenta-intense-bg {
  background-color: #a03196;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-cyan-intense-bg {
  background-color: #258f8f;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-white-intense-bg {
  background-color: #a1a6b2;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-default-inverse-fg {
  color: var(--jp-ui-inverse-font-color0);
}

.jp-RenderedText pre .ansi-default-inverse-bg {
  background-color: var(--jp-inverse-layout-color0);
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-bold {
  font-weight: bold;
}

.jp-RenderedText pre .ansi-underline {
  text-decoration: underline;
}

.jp-RenderedText[data-mime-type='application/vnd.jupyter.stderr'] {
  background: var(--jp-rendermime-error-background);
  padding-top: var(--jp-code-padding);
}

/*-----------------------------------------------------------------------------
| RenderedLatex
|----------------------------------------------------------------------------*/

.jp-RenderedLatex {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-content-font-size1);
  line-height: var(--jp-content-line-height);
}

/* Left-justify outputs.*/
.jp-OutputArea-output.jp-RenderedLatex {
  padding: var(--jp-code-padding);
  text-align: left;
}

/*-----------------------------------------------------------------------------
| RenderedHTML
|----------------------------------------------------------------------------*/

.jp-RenderedHTMLCommon {
  color: var(--jp-content-font-color1);
  font-family: var(--jp-content-font-family);
  font-size: var(--jp-content-font-size1);
  line-height: var(--jp-content-line-height);

  /* Give a bit more R padding on Markdown text to keep line lengths reasonable */
  padding-right: 20px;
}

.jp-RenderedHTMLCommon em {
  font-style: italic;
}

.jp-RenderedHTMLCommon strong {
  font-weight: bold;
}

.jp-RenderedHTMLCommon u {
  text-decoration: underline;
}

.jp-RenderedHTMLCommon a:link {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

.jp-RenderedHTMLCommon a:hover {
  text-decoration: underline;
  color: var(--jp-content-link-color);
}

.jp-RenderedHTMLCommon a:visited {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

/* Headings */

.jp-RenderedHTMLCommon h1,
.jp-RenderedHTMLCommon h2,
.jp-RenderedHTMLCommon h3,
.jp-RenderedHTMLCommon h4,
.jp-RenderedHTMLCommon h5,
.jp-RenderedHTMLCommon h6 {
  line-height: var(--jp-content-heading-line-height);
  font-weight: var(--jp-content-heading-font-weight);
  font-style: normal;
  margin: var(--jp-content-heading-margin-top) 0
    var(--jp-content-heading-margin-bottom) 0;
}

.jp-RenderedHTMLCommon h1:first-child,
.jp-RenderedHTMLCommon h2:first-child,
.jp-RenderedHTMLCommon h3:first-child,
.jp-RenderedHTMLCommon h4:first-child,
.jp-RenderedHTMLCommon h5:first-child,
.jp-RenderedHTMLCommon h6:first-child {
  margin-top: calc(0.5 * var(--jp-content-heading-margin-top));
}

.jp-RenderedHTMLCommon h1:last-child,
.jp-RenderedHTMLCommon h2:last-child,
.jp-RenderedHTMLCommon h3:last-child,
.jp-RenderedHTMLCommon h4:last-child,
.jp-RenderedHTMLCommon h5:last-child,
.jp-RenderedHTMLCommon h6:last-child {
  margin-bottom: calc(0.5 * var(--jp-content-heading-margin-bottom));
}

.jp-RenderedHTMLCommon h1 {
  font-size: var(--jp-content-font-size5);
}

.jp-RenderedHTMLCommon h2 {
  font-size: var(--jp-content-font-size4);
}

.jp-RenderedHTMLCommon h3 {
  font-size: var(--jp-content-font-size3);
}

.jp-RenderedHTMLCommon h4 {
  font-size: var(--jp-content-font-size2);
}

.jp-RenderedHTMLCommon h5 {
  font-size: var(--jp-content-font-size1);
}

.jp-RenderedHTMLCommon h6 {
  font-size: var(--jp-content-font-size0);
}

/* Lists */

/* stylelint-disable selector-max-type, selector-max-compound-selectors */

.jp-RenderedHTMLCommon ul:not(.list-inline),
.jp-RenderedHTMLCommon ol:not(.list-inline) {
  padding-left: 2em;
}

.jp-RenderedHTMLCommon ul {
  list-style: disc;
}

.jp-RenderedHTMLCommon ul ul {
  list-style: square;
}

.jp-RenderedHTMLCommon ul ul ul {
  list-style: circle;
}

.jp-RenderedHTMLCommon ol {
  list-style: decimal;
}

.jp-RenderedHTMLCommon ol ol {
  list-style: upper-alpha;
}

.jp-RenderedHTMLCommon ol ol ol {
  list-style: lower-alpha;
}

.jp-RenderedHTMLCommon ol ol ol ol {
  list-style: lower-roman;
}

.jp-RenderedHTMLCommon ol ol ol ol ol {
  list-style: decimal;
}

.jp-RenderedHTMLCommon ol,
.jp-RenderedHTMLCommon ul {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon ul ul,
.jp-RenderedHTMLCommon ul ol,
.jp-RenderedHTMLCommon ol ul,
.jp-RenderedHTMLCommon ol ol {
  margin-bottom: 0;
}

/* stylelint-enable selector-max-type, selector-max-compound-selectors */

.jp-RenderedHTMLCommon hr {
  color: var(--jp-border-color2);
  background-color: var(--jp-border-color1);
  margin-top: 1em;
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon > pre {
  margin: 1.5em 2em;
}

.jp-RenderedHTMLCommon pre,
.jp-RenderedHTMLCommon code {
  border: 0;
  background-color: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
  font-family: var(--jp-code-font-family);
  font-size: inherit;
  line-height: var(--jp-code-line-height);
  padding: 0;
  white-space: pre-wrap;
}

.jp-RenderedHTMLCommon :not(pre) > code {
  background-color: var(--jp-layout-color2);
  padding: 1px 5px;
}

/* Tables */

.jp-RenderedHTMLCommon table {
  border-collapse: collapse;
  border-spacing: 0;
  border: none;
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
  table-layout: fixed;
  margin-left: auto;
  margin-bottom: 1em;
  margin-right: auto;
}

.jp-RenderedHTMLCommon thead {
  border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
  vertical-align: bottom;
}

.jp-RenderedHTMLCommon td,
.jp-RenderedHTMLCommon th,
.jp-RenderedHTMLCommon tr {
  vertical-align: middle;
  padding: 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}

.jp-RenderedMarkdown.jp-RenderedHTMLCommon td,
.jp-RenderedMarkdown.jp-RenderedHTMLCommon th {
  max-width: none;
}

:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon td,
:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon th,
:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon tr {
  text-align: right;
}

.jp-RenderedHTMLCommon th {
  font-weight: bold;
}

.jp-RenderedHTMLCommon tbody tr:nth-child(odd) {
  background: var(--jp-layout-color0);
}

.jp-RenderedHTMLCommon tbody tr:nth-child(even) {
  background: var(--jp-rendermime-table-row-background);
}

.jp-RenderedHTMLCommon tbody tr:hover {
  background: var(--jp-rendermime-table-row-hover-background);
}

.jp-RenderedHTMLCommon p {
  text-align: left;
  margin: 0;
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon img {
  -moz-force-broken-image-icon: 1;
}

/* Restrict to direct children as other images could be nested in other content. */
.jp-RenderedHTMLCommon > img {
  display: block;
  margin-left: 0;
  margin-right: 0;
  margin-bottom: 1em;
}

/* Change color behind transparent images if they need it... */
[data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-light-background {
  background-color: var(--jp-inverse-layout-color1);
}

[data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-dark-background {
  background-color: var(--jp-inverse-layout-color1);
}

.jp-RenderedHTMLCommon img,
.jp-RenderedImage img,
.jp-RenderedHTMLCommon svg,
.jp-RenderedSVG svg {
  max-width: 100%;
  height: auto;
}

.jp-RenderedHTMLCommon img.jp-mod-unconfined,
.jp-RenderedImage img.jp-mod-unconfined,
.jp-RenderedHTMLCommon svg.jp-mod-unconfined,
.jp-RenderedSVG svg.jp-mod-unconfined {
  max-width: none;
}

.jp-RenderedHTMLCommon .alert {
  padding: var(--jp-notebook-padding);
  border: var(--jp-border-width) solid transparent;
  border-radius: var(--jp-border-radius);
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon .alert-info {
  color: var(--jp-info-color0);
  background-color: var(--jp-info-color3);
  border-color: var(--jp-info-color2);
}

.jp-RenderedHTMLCommon .alert-info hr {
  border-color: var(--jp-info-color3);
}

.jp-RenderedHTMLCommon .alert-info > p:last-child,
.jp-RenderedHTMLCommon .alert-info > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-warning {
  color: var(--jp-warn-color0);
  background-color: var(--jp-warn-color3);
  border-color: var(--jp-warn-color2);
}

.jp-RenderedHTMLCommon .alert-warning hr {
  border-color: var(--jp-warn-color3);
}

.jp-RenderedHTMLCommon .alert-warning > p:last-child,
.jp-RenderedHTMLCommon .alert-warning > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-success {
  color: var(--jp-success-color0);
  background-color: var(--jp-success-color3);
  border-color: var(--jp-success-color2);
}

.jp-RenderedHTMLCommon .alert-success hr {
  border-color: var(--jp-success-color3);
}

.jp-RenderedHTMLCommon .alert-success > p:last-child,
.jp-RenderedHTMLCommon .alert-success > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-danger {
  color: var(--jp-error-color0);
  background-color: var(--jp-error-color3);
  border-color: var(--jp-error-color2);
}

.jp-RenderedHTMLCommon .alert-danger hr {
  border-color: var(--jp-error-color3);
}

.jp-RenderedHTMLCommon .alert-danger > p:last-child,
.jp-RenderedHTMLCommon .alert-danger > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon blockquote {
  margin: 1em 2em;
  padding: 0 1em;
  border-left: 5px solid var(--jp-border-color2);
}

a.jp-InternalAnchorLink {
  visibility: hidden;
  margin-left: 8px;
  color: var(--md-blue-800);
}

h1:hover .jp-InternalAnchorLink,
h2:hover .jp-InternalAnchorLink,
h3:hover .jp-InternalAnchorLink,
h4:hover .jp-InternalAnchorLink,
h5:hover .jp-InternalAnchorLink,
h6:hover .jp-InternalAnchorLink {
  visibility: visible;
}

.jp-RenderedHTMLCommon kbd {
  background-color: var(--jp-rendermime-table-row-background);
  border: 1px solid var(--jp-border-color0);
  border-bottom-color: var(--jp-border-color2);
  border-radius: 3px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
  display: inline-block;
  font-size: var(--jp-ui-font-size0);
  line-height: 1em;
  padding: 0.2em 0.5em;
}

/* Most direct children of .jp-RenderedHTMLCommon have a margin-bottom of 1.0.
 * At the bottom of cells this is a bit too much as there is also spacing
 * between cells. Going all the way to 0 gets too tight between markdown and
 * code cells.
 */
.jp-RenderedHTMLCommon > *:last-child {
  margin-bottom: 0.5em;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

.lm-cursor-backdrop {
  position: fixed;
  width: 200px;
  height: 200px;
  margin-top: -100px;
  margin-left: -100px;
  will-change: transform;
  z-index: 100;
}

.lm-mod-drag-image {
  will-change: transform;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

.jp-lineFormSearch {
  padding: 4px 12px;
  background-color: var(--jp-layout-color2);
  box-shadow: var(--jp-toolbar-box-shadow);
  z-index: 2;
  font-size: var(--jp-ui-font-size1);
}

.jp-lineFormCaption {
  font-size: var(--jp-ui-font-size0);
  line-height: var(--jp-ui-font-size1);
  margin-top: 4px;
  color: var(--jp-ui-font-color0);
}

.jp-baseLineForm {
  border: none;
  border-radius: 0;
  position: absolute;
  background-size: 16px;
  background-repeat: no-repeat;
  background-position: center;
  outline: none;
}

.jp-lineFormButtonContainer {
  top: 4px;
  right: 8px;
  height: 24px;
  padding: 0 12px;
  width: 12px;
}

.jp-lineFormButtonIcon {
  top: 0;
  right: 0;
  background-color: var(--jp-brand-color1);
  height: 100%;
  width: 100%;
  box-sizing: border-box;
  padding: 4px 6px;
}

.jp-lineFormButton {
  top: 0;
  right: 0;
  background-color: transparent;
  height: 100%;
  width: 100%;
  box-sizing: border-box;
}

.jp-lineFormWrapper {
  overflow: hidden;
  padding: 0 8px;
  border: 1px solid var(--jp-border-color0);
  background-color: var(--jp-input-active-background);
  height: 22px;
}

.jp-lineFormWrapperFocusWithin {
  border: var(--jp-border-width) solid var(--md-blue-500);
  box-shadow: inset 0 0 4px var(--md-blue-300);
}

.jp-lineFormInput {
  background: transparent;
  width: 200px;
  height: 100%;
  border: none;
  outline: none;
  color: var(--jp-ui-font-color0);
  line-height: 28px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-JSONEditor {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.jp-JSONEditor-host {
  flex: 1 1 auto;
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  border-radius: 0;
  background: var(--jp-layout-color0);
  min-height: 50px;
  padding: 1px;
}

.jp-JSONEditor.jp-mod-error .jp-JSONEditor-host {
  border-color: red;
  outline-color: red;
}

.jp-JSONEditor-header {
  display: flex;
  flex: 1 0 auto;
  padding: 0 0 0 12px;
}

.jp-JSONEditor-header label {
  flex: 0 0 auto;
}

.jp-JSONEditor-commitButton {
  height: 16px;
  width: 16px;
  background-size: 18px;
  background-repeat: no-repeat;
  background-position: center;
}

.jp-JSONEditor-host.jp-mod-focused {
  background-color: var(--jp-input-active-background);
  border: 1px solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
}

.jp-Editor.jp-mod-dropTarget {
  border: var(--jp-border-width) solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/
.jp-DocumentSearch-input {
  border: none;
  outline: none;
  color: var(--jp-ui-font-color0);
  font-size: var(--jp-ui-font-size1);
  background-color: var(--jp-layout-color0);
  font-family: var(--jp-ui-font-family);
  padding: 2px 1px;
  resize: none;
}

.jp-DocumentSearch-overlay {
  position: absolute;
  background-color: var(--jp-toolbar-background);
  border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  border-left: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  top: 0;
  right: 0;
  z-index: 7;
  min-width: 405px;
  padding: 2px;
  font-size: var(--jp-ui-font-size1);

  --jp-private-document-search-button-height: 20px;
}

.jp-DocumentSearch-overlay button {
  background-color: var(--jp-toolbar-background);
  outline: 0;
}

.jp-DocumentSearch-overlay button:hover {
  background-color: var(--jp-layout-color2);
}

.jp-DocumentSearch-overlay button:active {
  background-color: var(--jp-layout-color3);
}

.jp-DocumentSearch-overlay-row {
  display: flex;
  align-items: center;
  margin-bottom: 2px;
}

.jp-DocumentSearch-button-content {
  display: inline-block;
  cursor: pointer;
  box-sizing: border-box;
  width: 100%;
  height: 100%;
}

.jp-DocumentSearch-button-content svg {
  width: 100%;
  height: 100%;
}

.jp-DocumentSearch-input-wrapper {
  border: var(--jp-border-width) solid var(--jp-border-color0);
  display: flex;
  background-color: var(--jp-layout-color0);
  margin: 2px;
}

.jp-DocumentSearch-input-wrapper:focus-within {
  border-color: var(--jp-cell-editor-active-border-color);
}

.jp-DocumentSearch-toggle-wrapper,
.jp-DocumentSearch-button-wrapper {
  all: initial;
  overflow: hidden;
  display: inline-block;
  border: none;
  box-sizing: border-box;
}

.jp-DocumentSearch-toggle-wrapper {
  width: 14px;
  height: 14px;
}

.jp-DocumentSearch-button-wrapper {
  width: var(--jp-private-document-search-button-height);
  height: var(--jp-private-document-search-button-height);
}

.jp-DocumentSearch-toggle-wrapper:focus,
.jp-DocumentSearch-button-wrapper:focus {
  outline: var(--jp-border-width) solid
    var(--jp-cell-editor-active-border-color);
  outline-offset: -1px;
}

.jp-DocumentSearch-toggle-wrapper,
.jp-DocumentSearch-button-wrapper,
.jp-DocumentSearch-button-content:focus {
  outline: none;
}

.jp-DocumentSearch-toggle-placeholder {
  width: 5px;
}

.jp-DocumentSearch-input-button::before {
  display: block;
  padding-top: 100%;
}

.jp-DocumentSearch-input-button-off {
  opacity: var(--jp-search-toggle-off-opacity);
}

.jp-DocumentSearch-input-button-off:hover {
  opacity: var(--jp-search-toggle-hover-opacity);
}

.jp-DocumentSearch-input-button-on {
  opacity: var(--jp-search-toggle-on-opacity);
}

.jp-DocumentSearch-index-counter {
  padding-left: 10px;
  padding-right: 10px;
  user-select: none;
  min-width: 35px;
  display: inline-block;
}

.jp-DocumentSearch-up-down-wrapper {
  display: inline-block;
  padding-right: 2px;
  margin-left: auto;
  white-space: nowrap;
}

.jp-DocumentSearch-spacer {
  margin-left: auto;
}

.jp-DocumentSearch-up-down-wrapper button {
  outline: 0;
  border: none;
  width: var(--jp-private-document-search-button-height);
  height: var(--jp-private-document-search-button-height);
  vertical-align: middle;
  margin: 1px 5px 2px;
}

.jp-DocumentSearch-up-down-button:hover {
  background-color: var(--jp-layout-color2);
}

.jp-DocumentSearch-up-down-button:active {
  background-color: var(--jp-layout-color3);
}

.jp-DocumentSearch-filter-button {
  border-radius: var(--jp-border-radius);
}

.jp-DocumentSearch-filter-button:hover {
  background-color: var(--jp-layout-color2);
}

.jp-DocumentSearch-filter-button-enabled {
  background-color: var(--jp-layout-color2);
}

.jp-DocumentSearch-filter-button-enabled:hover {
  background-color: var(--jp-layout-color3);
}

.jp-DocumentSearch-search-options {
  padding: 0 8px;
  margin-left: 3px;
  width: 100%;
  display: grid;
  justify-content: start;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  justify-items: stretch;
}

.jp-DocumentSearch-search-filter-disabled {
  color: var(--jp-ui-font-color2);
}

.jp-DocumentSearch-search-filter {
  display: flex;
  align-items: center;
  user-select: none;
}

.jp-DocumentSearch-regex-error {
  color: var(--jp-error-color0);
}

.jp-DocumentSearch-replace-button-wrapper {
  overflow: hidden;
  display: inline-block;
  box-sizing: border-box;
  border: var(--jp-border-width) solid var(--jp-border-color0);
  margin: auto 2px;
  padding: 1px 4px;
  height: calc(var(--jp-private-document-search-button-height) + 2px);
}

.jp-DocumentSearch-replace-button-wrapper:focus {
  border: var(--jp-border-width) solid var(--jp-cell-editor-active-border-color);
}

.jp-DocumentSearch-replace-button {
  display: inline-block;
  text-align: center;
  cursor: pointer;
  box-sizing: border-box;
  color: var(--jp-ui-font-color1);

  /* height - 2 * (padding of wrapper) */
  line-height: calc(var(--jp-private-document-search-button-height) - 2px);
  width: 100%;
  height: 100%;
}

.jp-DocumentSearch-replace-button:focus {
  outline: none;
}

.jp-DocumentSearch-replace-wrapper-class {
  margin-left: 14px;
  display: flex;
}

.jp-DocumentSearch-replace-toggle {
  border: none;
  background-color: var(--jp-toolbar-background);
  border-radius: var(--jp-border-radius);
}

.jp-DocumentSearch-replace-toggle:hover {
  background-color: var(--jp-layout-color2);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.cm-editor {
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  font-family: var(--jp-code-font-family);
  border: 0;
  border-radius: 0;
  height: auto;

  /* Changed to auto to autogrow */
}

.cm-editor pre {
  padding: 0 var(--jp-code-padding);
}

.jp-CodeMirrorEditor[data-type='inline'] .cm-dialog {
  background-color: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
}

.jp-CodeMirrorEditor {
  cursor: text;
}

/* When zoomed out 67% and 33% on a screen of 1440 width x 900 height */
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .jp-CodeMirrorEditor[data-type='inline'] .cm-cursor {
    border-left: var(--jp-code-cursor-width1) solid
      var(--jp-editor-cursor-color);
  }
}

/* When zoomed out less than 33% */
@media screen and (min-width: 4320px) {
  .jp-CodeMirrorEditor[data-type='inline'] .cm-cursor {
    border-left: var(--jp-code-cursor-width2) solid
      var(--jp-editor-cursor-color);
  }
}

.cm-editor.jp-mod-readOnly .cm-cursor {
  display: none;
}

.jp-CollaboratorCursor {
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: none;
  border-bottom: 3px solid;
  background-clip: content-box;
  margin-left: -5px;
  margin-right: -5px;
}

.cm-searching,
.cm-searching span {
  /* `.cm-searching span`: we need to override syntax highlighting */
  background-color: var(--jp-search-unselected-match-background-color);
  color: var(--jp-search-unselected-match-color);
}

.cm-searching::selection,
.cm-searching span::selection {
  background-color: var(--jp-search-unselected-match-background-color);
  color: var(--jp-search-unselected-match-color);
}

.jp-current-match > .cm-searching,
.jp-current-match > .cm-searching span,
.cm-searching > .jp-current-match,
.cm-searching > .jp-current-match span {
  background-color: var(--jp-search-selected-match-background-color);
  color: var(--jp-search-selected-match-color);
}

.jp-current-match > .cm-searching::selection,
.cm-searching > .jp-current-match::selection,
.jp-current-match > .cm-searching span::selection {
  background-color: var(--jp-search-selected-match-background-color);
  color: var(--jp-search-selected-match-color);
}

.cm-trailingspace {
  background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAgAAAAFCAYAAAB4ka1VAAAAsElEQVQIHQGlAFr/AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA7+r3zKmT0/+pk9P/7+r3zAAAAAAAAAAABAAAAAAAAAAA6OPzM+/q9wAAAAAA6OPzMwAAAAAAAAAAAgAAAAAAAAAAGR8NiRQaCgAZIA0AGR8NiQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAQyoYJ/SY80UAAAAASUVORK5CYII=);
  background-position: center left;
  background-repeat: repeat-x;
}

.jp-CollaboratorCursor-hover {
  position: absolute;
  z-index: 1;
  transform: translateX(-50%);
  color: white;
  border-radius: 3px;
  padding-left: 4px;
  padding-right: 4px;
  padding-top: 1px;
  padding-bottom: 1px;
  text-align: center;
  font-size: var(--jp-ui-font-size1);
  white-space: nowrap;
}

.jp-CodeMirror-ruler {
  border-left: 1px dashed var(--jp-border-color2);
}

/* Styles for shared cursors (remote cursor locations and selected ranges) */
.jp-CodeMirrorEditor .cm-ySelectionCaret {
  position: relative;
  border-left: 1px solid black;
  margin-left: -1px;
  margin-right: -1px;
  box-sizing: border-box;
}

.jp-CodeMirrorEditor .cm-ySelectionCaret > .cm-ySelectionInfo {
  white-space: nowrap;
  position: absolute;
  top: -1.15em;
  padding-bottom: 0.05em;
  left: -1px;
  font-size: 0.95em;
  font-family: var(--jp-ui-font-family);
  font-weight: bold;
  line-height: normal;
  user-select: none;
  color: white;
  padding-left: 2px;
  padding-right: 2px;
  z-index: 101;
  transition: opacity 0.3s ease-in-out;
}

.jp-CodeMirrorEditor .cm-ySelectionInfo {
  transition-delay: 0.7s;
  opacity: 0;
}

.jp-CodeMirrorEditor .cm-ySelectionCaret:hover > .cm-ySelectionInfo {
  opacity: 1;
  transition-delay: 0s;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-MimeDocument {
  outline: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-filebrowser-button-height: 28px;
  --jp-private-filebrowser-button-width: 48px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-FileBrowser .jp-SidePanel-content {
  display: flex;
  flex-direction: column;
}

.jp-FileBrowser-toolbar.jp-Toolbar {
  flex-wrap: wrap;
  row-gap: 12px;
  border-bottom: none;
  height: auto;
  margin: 8px 12px 0;
  box-shadow: none;
  padding: 0;
  justify-content: flex-start;
}

.jp-FileBrowser-Panel {
  flex: 1 1 auto;
  display: flex;
  flex-direction: column;
}

.jp-BreadCrumbs {
  flex: 0 0 auto;
  margin: 8px 12px;
}

.jp-BreadCrumbs-item {
  margin: 0 2px;
  padding: 0 2px;
  border-radius: var(--jp-border-radius);
  cursor: pointer;
}

.jp-BreadCrumbs-item:hover {
  background-color: var(--jp-layout-color2);
}

.jp-BreadCrumbs-item:first-child {
  margin-left: 0;
}

.jp-BreadCrumbs-item.jp-mod-dropTarget {
  background-color: var(--jp-brand-color2);
  opacity: 0.7;
}

/*-----------------------------------------------------------------------------
| Buttons
|----------------------------------------------------------------------------*/

.jp-FileBrowser-toolbar > .jp-Toolbar-item {
  flex: 0 0 auto;
  padding-left: 0;
  padding-right: 2px;
  align-items: center;
  height: unset;
}

.jp-FileBrowser-toolbar > .jp-Toolbar-item .jp-ToolbarButtonComponent {
  width: 40px;
}

/*-----------------------------------------------------------------------------
| Other styles
|----------------------------------------------------------------------------*/

.jp-FileDialog.jp-mod-conflict input {
  color: var(--jp-error-color1);
}

.jp-FileDialog .jp-new-name-title {
  margin-top: 12px;
}

.jp-LastModified-hidden {
  display: none;
}

.jp-FileSize-hidden {
  display: none;
}

.jp-FileBrowser .lm-AccordionPanel > h3:first-child {
  display: none;
}

/*-----------------------------------------------------------------------------
| DirListing
|----------------------------------------------------------------------------*/

.jp-DirListing {
  flex: 1 1 auto;
  display: flex;
  flex-direction: column;
  outline: 0;
}

.jp-DirListing-header {
  flex: 0 0 auto;
  display: flex;
  flex-direction: row;
  align-items: center;
  overflow: hidden;
  border-top: var(--jp-border-width) solid var(--jp-border-color2);
  border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
  box-shadow: var(--jp-toolbar-box-shadow);
  z-index: 2;
}

.jp-DirListing-headerItem {
  padding: 4px 12px 2px;
  font-weight: 500;
}

.jp-DirListing-headerItem:hover {
  background: var(--jp-layout-color2);
}

.jp-DirListing-headerItem.jp-id-name {
  flex: 1 0 84px;
}

.jp-DirListing-headerItem.jp-id-modified {
  flex: 0 0 112px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
}

.jp-DirListing-headerItem.jp-id-filesize {
  flex: 0 0 75px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
}

.jp-id-narrow {
  display: none;
  flex: 0 0 5px;
  padding: 4px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
  color: var(--jp-border-color2);
}

.jp-DirListing-narrow .jp-id-narrow {
  display: block;
}

.jp-DirListing-narrow .jp-id-modified,
.jp-DirListing-narrow .jp-DirListing-itemModified {
  display: none;
}

.jp-DirListing-headerItem.jp-mod-selected {
  font-weight: 600;
}

/* increase specificity to override bundled default */
.jp-DirListing-content {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  list-style-type: none;
  overflow: auto;
  background-color: var(--jp-layout-color1);
}

.jp-DirListing-content mark {
  color: var(--jp-ui-font-color0);
  background-color: transparent;
  font-weight: bold;
}

.jp-DirListing-content .jp-DirListing-item.jp-mod-selected mark {
  color: var(--jp-ui-inverse-font-color0);
}

/* Style the directory listing content when a user drops a file to upload */
.jp-DirListing.jp-mod-native-drop .jp-DirListing-content {
  outline: 5px dashed rgba(128, 128, 128, 0.5);
  outline-offset: -10px;
  cursor: copy;
}

.jp-DirListing-item {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 4px 12px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.jp-DirListing-checkboxWrapper {
  /* Increases hit area of checkbox. */
  padding: 4px;
}

.jp-DirListing-header
  .jp-DirListing-checkboxWrapper
  + .jp-DirListing-headerItem {
  padding-left: 4px;
}

.jp-DirListing-content .jp-DirListing-checkboxWrapper {
  position: relative;
  left: -4px;
  margin: -4px 0 -4px -8px;
}

.jp-DirListing-checkboxWrapper.jp-mod-visible {
  visibility: visible;
}

/* For devices that support hovering, hide checkboxes until hovered, selected...
*/
@media (hover: hover) {
  .jp-DirListing-checkboxWrapper {
    visibility: hidden;
  }

  .jp-DirListing-item:hover .jp-DirListing-checkboxWrapper,
  .jp-DirListing-item.jp-mod-selected .jp-DirListing-checkboxWrapper {
    visibility: visible;
  }
}

.jp-DirListing-item[data-is-dot] {
  opacity: 75%;
}

.jp-DirListing-item.jp-mod-selected {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.jp-DirListing-item.jp-mod-dropTarget {
  background: var(--jp-brand-color3);
}

.jp-DirListing-item:hover:not(.jp-mod-selected) {
  background: var(--jp-layout-color2);
}

.jp-DirListing-itemIcon {
  flex: 0 0 20px;
  margin-right: 4px;
}

.jp-DirListing-itemText {
  flex: 1 0 64px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  user-select: none;
}

.jp-DirListing-itemText:focus {
  outline-width: 2px;
  outline-color: var(--jp-inverse-layout-color1);
  outline-style: solid;
  outline-offset: 1px;
}

.jp-DirListing-item.jp-mod-selected .jp-DirListing-itemText:focus {
  outline-color: var(--jp-layout-color1);
}

.jp-DirListing-itemModified {
  flex: 0 0 125px;
  text-align: right;
}

.jp-DirListing-itemFileSize {
  flex: 0 0 90px;
  text-align: right;
}

.jp-DirListing-editor {
  flex: 1 0 64px;
  outline: none;
  border: none;
  color: var(--jp-ui-font-color1);
  background-color: var(--jp-layout-color1);
}

.jp-DirListing-item.jp-mod-running .jp-DirListing-itemIcon::before {
  color: var(--jp-success-color1);
  content: '\25CF';
  font-size: 8px;
  position: absolute;
  left: -8px;
}

.jp-DirListing-item.jp-mod-running.jp-mod-selected
  .jp-DirListing-itemIcon::before {
  color: var(--jp-ui-inverse-font-color1);
}

.jp-DirListing-item.lm-mod-drag-image,
.jp-DirListing-item.jp-mod-selected.lm-mod-drag-image {
  font-size: var(--jp-ui-font-size1);
  padding-left: 4px;
  margin-left: 4px;
  width: 160px;
  background-color: var(--jp-ui-inverse-font-color2);
  box-shadow: var(--jp-elevation-z2);
  border-radius: 0;
  color: var(--jp-ui-font-color1);
  transform: translateX(-40%) translateY(-58%);
}

.jp-Document {
  min-width: 120px;
  min-height: 120px;
  outline: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Main OutputArea
| OutputArea has a list of Outputs
|----------------------------------------------------------------------------*/

.jp-OutputArea {
  overflow-y: auto;
}

.jp-OutputArea-child {
  display: table;
  table-layout: fixed;
  width: 100%;
  overflow: hidden;
}

.jp-OutputPrompt {
  width: var(--jp-cell-prompt-width);
  color: var(--jp-cell-outprompt-font-color);
  font-family: var(--jp-cell-prompt-font-family);
  padding: var(--jp-code-padding);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
  opacity: var(--jp-cell-prompt-opacity);

  /* Right align prompt text, don't wrap to handle large prompt numbers */
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;

  /* Disable text selection */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.jp-OutputArea-prompt {
  display: table-cell;
  vertical-align: top;
}

.jp-OutputArea-output {
  display: table-cell;
  width: 100%;
  height: auto;
  overflow: auto;
  user-select: text;
  -moz-user-select: text;
  -webkit-user-select: text;
  -ms-user-select: text;
}

.jp-OutputArea .jp-RenderedText {
  padding-left: 1ch;
}

/**
 * Prompt overlay.
 */

.jp-OutputArea-promptOverlay {
  position: absolute;
  top: 0;
  width: var(--jp-cell-prompt-width);
  height: 100%;
  opacity: 0.5;
}

.jp-OutputArea-promptOverlay:hover {
  background: var(--jp-layout-color2);
  box-shadow: inset 0 0 1px var(--jp-inverse-layout-color0);
  cursor: zoom-out;
}

.jp-mod-outputsScrolled .jp-OutputArea-promptOverlay:hover {
  cursor: zoom-in;
}

/**
 * Isolated output.
 */
.jp-OutputArea-output.jp-mod-isolated {
  width: 100%;
  display: block;
}

/*
When drag events occur, `lm-mod-override-cursor` is added to the body.
Because iframes steal all cursor events, the following two rules are necessary
to suppress pointer events while resize drags are occurring. There may be a
better solution to this problem.
*/
body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated {
  position: relative;
}

body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
}

/* pre */

.jp-OutputArea-output pre {
  border: none;
  margin: 0;
  padding: 0;
  overflow-x: auto;
  overflow-y: auto;
  word-break: break-all;
  word-wrap: break-word;
  white-space: pre-wrap;
}

/* tables */

.jp-OutputArea-output.jp-RenderedHTMLCommon table {
  margin-left: 0;
  margin-right: 0;
}

/* description lists */

.jp-OutputArea-output dl,
.jp-OutputArea-output dt,
.jp-OutputArea-output dd {
  display: block;
}

.jp-OutputArea-output dl {
  width: 100%;
  overflow: hidden;
  padding: 0;
  margin: 0;
}

.jp-OutputArea-output dt {
  font-weight: bold;
  float: left;
  width: 20%;
  padding: 0;
  margin: 0;
}

.jp-OutputArea-output dd {
  float: left;
  width: 80%;
  padding: 0;
  margin: 0;
}

.jp-TrimmedOutputs pre {
  background: var(--jp-layout-color3);
  font-size: calc(var(--jp-code-font-size) * 1.4);
  text-align: center;
  text-transform: uppercase;
}

/* Hide the gutter in case of
 *  - nested output areas (e.g. in the case of output widgets)
 *  - mirrored output areas
 */
.jp-OutputArea .jp-OutputArea .jp-OutputArea-prompt {
  display: none;
}

/* Hide empty lines in the output area, for instance due to cleared widgets */
.jp-OutputArea-prompt:empty {
  padding: 0;
  border: 0;
}

/*-----------------------------------------------------------------------------
| executeResult is added to any Output-result for the display of the object
| returned by a cell
|----------------------------------------------------------------------------*/

.jp-OutputArea-output.jp-OutputArea-executeResult {
  margin-left: 0;
  width: 100%;
}

/* Text output with the Out[] prompt needs a top padding to match the
 * alignment of the Out[] prompt itself.
 */
.jp-OutputArea-executeResult .jp-RenderedText.jp-OutputArea-output {
  padding-top: var(--jp-code-padding);
  border-top: var(--jp-border-width) solid transparent;
}

/*-----------------------------------------------------------------------------
| The Stdin output
|----------------------------------------------------------------------------*/

.jp-Stdin-prompt {
  color: var(--jp-content-font-color0);
  padding-right: var(--jp-code-padding);
  vertical-align: baseline;
  flex: 0 0 auto;
}

.jp-Stdin-input {
  font-family: var(--jp-code-font-family);
  font-size: inherit;
  color: inherit;
  background-color: inherit;
  width: 42%;
  min-width: 200px;

  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;

  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0 0.25em;
  margin: 0 0.25em;
  flex: 0 0 70%;
}

.jp-Stdin-input::placeholder {
  opacity: 0;
}

.jp-Stdin-input:focus {
  box-shadow: none;
}

.jp-Stdin-input:focus::placeholder {
  opacity: 1;
}

/*-----------------------------------------------------------------------------
| Output Area View
|----------------------------------------------------------------------------*/

.jp-LinkedOutputView .jp-OutputArea {
  height: 100%;
  display: block;
}

.jp-LinkedOutputView .jp-OutputArea-output:only-child {
  height: 100%;
}

/*-----------------------------------------------------------------------------
| Printing
|----------------------------------------------------------------------------*/

@media print {
  .jp-OutputArea-child {
    break-inside: avoid-page;
  }
}

/*-----------------------------------------------------------------------------
| Mobile
|----------------------------------------------------------------------------*/
@media only screen and (max-width: 760px) {
  .jp-OutputPrompt {
    display: table-row;
    text-align: left;
  }

  .jp-OutputArea-child .jp-OutputArea-output {
    display: table-row;
    margin-left: var(--jp-notebook-padding);
  }
}

/* Trimmed outputs warning */
.jp-TrimmedOutputs > a {
  margin: 10px;
  text-decoration: none;
  cursor: pointer;
}

.jp-TrimmedOutputs > a:hover {
  text-decoration: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Table of Contents
|----------------------------------------------------------------------------*/

:root {
  --jp-private-toc-active-width: 4px;
}

.jp-TableOfContents {
  display: flex;
  flex-direction: column;
  background: var(--jp-layout-color1);
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
  height: 100%;
}

.jp-TableOfContents-placeholder {
  text-align: center;
}

.jp-TableOfContents-placeholderContent {
  color: var(--jp-content-font-color2);
  padding: 8px;
}

.jp-TableOfContents-placeholderContent > h3 {
  margin-bottom: var(--jp-content-heading-margin-bottom);
}

.jp-TableOfContents .jp-SidePanel-content {
  overflow-y: auto;
}

.jp-TableOfContents-tree {
  margin: 4px;
}

.jp-TableOfContents ol {
  list-style-type: none;
}

/* stylelint-disable-next-line selector-max-type */
.jp-TableOfContents li > ol {
  /* Align left border with triangle icon center */
  padding-left: 11px;
}

.jp-TableOfContents-content {
  /* left margin for the active heading indicator */
  margin: 0 0 0 var(--jp-private-toc-active-width);
  padding: 0;
  background-color: var(--jp-layout-color1);
}

.jp-tocItem {
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.jp-tocItem-heading {
  display: flex;
  cursor: pointer;
}

.jp-tocItem-heading:hover {
  background-color: var(--jp-layout-color2);
}

.jp-tocItem-content {
  display: block;
  padding: 4px 0;
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow-x: hidden;
}

.jp-tocItem-collapser {
  height: 20px;
  margin: 2px 2px 0;
  padding: 0;
  background: none;
  border: none;
  cursor: pointer;
}

.jp-tocItem-collapser:hover {
  background-color: var(--jp-layout-color3);
}

/* Active heading indicator */

.jp-tocItem-heading::before {
  content: ' ';
  background: transparent;
  width: var(--jp-private-toc-active-width);
  height: 24px;
  position: absolute;
  left: 0;
  border-radius: var(--jp-border-radius);
}

.jp-tocItem-heading.jp-tocItem-active::before {
  background-color: var(--jp-brand-color1);
}

.jp-tocItem-heading:hover.jp-tocItem-active::before {
  background: var(--jp-brand-color0);
  opacity: 1;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Collapser {
  flex: 0 0 var(--jp-cell-collapser-width);
  padding: 0;
  margin: 0;
  border: none;
  outline: none;
  background: transparent;
  border-radius: var(--jp-border-radius);
  opacity: 1;
}

.jp-Collapser-child {
  display: block;
  width: 100%;
  box-sizing: border-box;

  /* height: 100% doesn't work because the height of its parent is computed from content */
  position: absolute;
  top: 0;
  bottom: 0;
}

/*-----------------------------------------------------------------------------
| Printing
|----------------------------------------------------------------------------*/

/*
Hiding collapsers in print mode.

Note: input and output wrappers have "display: block" propery in print mode.
*/

@media print {
  .jp-Collapser {
    display: none;
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Header/Footer
|----------------------------------------------------------------------------*/

/* Hidden by zero height by default */
.jp-CellHeader,
.jp-CellFooter {
  height: 0;
  width: 100%;
  padding: 0;
  margin: 0;
  border: none;
  outline: none;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Input
|----------------------------------------------------------------------------*/

/* All input areas */
.jp-InputArea {
  display: table;
  table-layout: fixed;
  width: 100%;
  overflow: hidden;
}

.jp-InputArea-editor {
  display: table-cell;
  overflow: hidden;
  vertical-align: top;

  /* This is the non-active, default styling */
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  border-radius: 0;
  background: var(--jp-cell-editor-background);
}

.jp-InputPrompt {
  display: table-cell;
  vertical-align: top;
  width: var(--jp-cell-prompt-width);
  color: var(--jp-cell-inprompt-font-color);
  font-family: var(--jp-cell-prompt-font-family);
  padding: var(--jp-code-padding);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  opacity: var(--jp-cell-prompt-opacity);
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;

  /* Right align prompt text, don't wrap to handle large prompt numbers */
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;

  /* Disable text selection */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/*-----------------------------------------------------------------------------
| Mobile
|----------------------------------------------------------------------------*/
@media only screen and (max-width: 760px) {
  .jp-InputArea-editor {
    display: table-row;
    margin-left: var(--jp-notebook-padding);
  }

  .jp-InputPrompt {
    display: table-row;
    text-align: left;
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Placeholder
|----------------------------------------------------------------------------*/

.jp-Placeholder {
  display: table;
  table-layout: fixed;
  width: 100%;
}

.jp-Placeholder-prompt {
  display: table-cell;
  box-sizing: border-box;
}

.jp-Placeholder-content {
  display: table-cell;
  padding: 4px 6px;
  border: 1px solid transparent;
  border-radius: 0;
  background: none;
  box-sizing: border-box;
  cursor: pointer;
}

.jp-Placeholder-contentContainer {
  display: flex;
}

.jp-Placeholder-content:hover,
.jp-InputPlaceholder > .jp-Placeholder-content:hover {
  border-color: var(--jp-layout-color3);
}

.jp-Placeholder-content .jp-MoreHorizIcon {
  width: 32px;
  height: 16px;
  border: 1px solid transparent;
  border-radius: var(--jp-border-radius);
}

.jp-Placeholder-content .jp-MoreHorizIcon:hover {
  border: 1px solid var(--jp-border-color1);
  box-shadow: 0 0 2px 0 rgba(0, 0, 0, 0.25);
  background-color: var(--jp-layout-color0);
}

.jp-PlaceholderText {
  white-space: nowrap;
  overflow-x: hidden;
  color: var(--jp-inverse-layout-color3);
  font-family: var(--jp-code-font-family);
}

.jp-InputPlaceholder > .jp-Placeholder-content {
  border-color: var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-cell-scrolling-output-offset: 5px;
}

/*-----------------------------------------------------------------------------
| Cell
|----------------------------------------------------------------------------*/

.jp-Cell {
  padding: var(--jp-cell-padding);
  margin: 0;
  border: none;
  outline: none;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Common input/output
|----------------------------------------------------------------------------*/

.jp-Cell-inputWrapper,
.jp-Cell-outputWrapper {
  display: flex;
  flex-direction: row;
  padding: 0;
  margin: 0;

  /* Added to reveal the box-shadow on the input and output collapsers. */
  overflow: visible;
}

/* Only input/output areas inside cells */
.jp-Cell-inputArea,
.jp-Cell-outputArea {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Collapser
|----------------------------------------------------------------------------*/

/* Make the output collapser disappear when there is not output, but do so
 * in a manner that leaves it in the layout and preserves its width.
 */
.jp-Cell.jp-mod-noOutputs .jp-Cell-outputCollapser {
  border: none !important;
  background: transparent !important;
}

.jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputCollapser {
  min-height: var(--jp-cell-collapser-min-height);
}

/*-----------------------------------------------------------------------------
| Output
|----------------------------------------------------------------------------*/

/* Put a space between input and output when there IS output */
.jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputWrapper {
  margin-top: 5px;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea {
  overflow-y: auto;
  max-height: 24em;
  margin-left: var(--jp-private-cell-scrolling-output-offset);
  resize: vertical;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea[style*='height'] {
  max-height: unset;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea::after {
  content: ' ';
  box-shadow: inset 0 0 6px 2px rgb(0 0 0 / 30%);
  width: 100%;
  height: 100%;
  position: sticky;
  bottom: 0;
  top: 0;
  margin-top: -50%;
  float: left;
  display: block;
  pointer-events: none;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-child {
  padding-top: 6px;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-prompt {
  width: calc(
    var(--jp-cell-prompt-width) - var(--jp-private-cell-scrolling-output-offset)
  );
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-promptOverlay {
  left: calc(-1 * var(--jp-private-cell-scrolling-output-offset));
}

/*-----------------------------------------------------------------------------
| CodeCell
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| MarkdownCell
|----------------------------------------------------------------------------*/

.jp-MarkdownOutput {
  display: table-cell;
  width: 100%;
  margin-top: 0;
  margin-bottom: 0;
  padding-left: var(--jp-code-padding);
}

.jp-MarkdownOutput.jp-RenderedHTMLCommon {
  overflow: auto;
}

/* collapseHeadingButton (show always if hiddenCellsButton is _not_ shown) */
.jp-collapseHeadingButton {
  display: flex;
  min-height: var(--jp-cell-collapser-min-height);
  font-size: var(--jp-code-font-size);
  position: absolute;
  background-color: transparent;
  background-size: 25px;
  background-repeat: no-repeat;
  background-position-x: center;
  background-position-y: top;
  background-image: var(--jp-icon-caret-down);
  right: 0;
  top: 0;
  bottom: 0;
}

.jp-collapseHeadingButton.jp-mod-collapsed {
  background-image: var(--jp-icon-caret-right);
}

/*
 set the container font size to match that of content
 so that the nested collapse buttons have the right size
*/
.jp-MarkdownCell .jp-InputPrompt {
  font-size: var(--jp-content-font-size1);
}

/*
  Align collapseHeadingButton with cell top header
  The font sizes are identical to the ones in packages/rendermime/style/base.css
*/
.jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='1'] {
  font-size: var(--jp-content-font-size5);
  background-position-y: calc(0.3 * var(--jp-content-font-size5));
}

.jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='2'] {
  font-size: var(--jp-content-font-size4);
  background-position-y: calc(0.3 * var(--jp-content-font-size4));
}

.jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='3'] {
  font-size: var(--jp-content-font-size3);
  background-position-y: calc(0.3 * var(--jp-content-font-size3));
}

.jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='4'] {
  font-size: var(--jp-content-font-size2);
  background-position-y: calc(0.3 * var(--jp-content-font-size2));
}

.jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='5'] {
  font-size: var(--jp-content-font-size1);
  background-position-y: top;
}

.jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='6'] {
  font-size: var(--jp-content-font-size0);
  background-position-y: top;
}

/* collapseHeadingButton (show only on (hover,active) if hiddenCellsButton is shown) */
.jp-Notebook.jp-mod-showHiddenCellsButton .jp-collapseHeadingButton {
  display: none;
}

.jp-Notebook.jp-mod-showHiddenCellsButton
  :is(.jp-MarkdownCell:hover, .jp-mod-active)
  .jp-collapseHeadingButton {
  display: flex;
}

/* showHiddenCellsButton (only show if jp-mod-showHiddenCellsButton is set, which
is a consequence of the showHiddenCellsButton option in Notebook Settings)*/
.jp-Notebook.jp-mod-showHiddenCellsButton .jp-showHiddenCellsButton {
  margin-left: calc(var(--jp-cell-prompt-width) + 2 * var(--jp-code-padding));
  margin-top: var(--jp-code-padding);
  border: 1px solid var(--jp-border-color2);
  background-color: var(--jp-border-color3) !important;
  color: var(--jp-content-font-color0) !important;
  display: flex;
}

.jp-Notebook.jp-mod-showHiddenCellsButton .jp-showHiddenCellsButton:hover {
  background-color: var(--jp-border-color2) !important;
}

.jp-showHiddenCellsButton {
  display: none;
}

/*-----------------------------------------------------------------------------
| Printing
|----------------------------------------------------------------------------*/

/*
Using block instead of flex to allow the use of the break-inside CSS property for
cell outputs.
*/

@media print {
  .jp-Cell-inputWrapper,
  .jp-Cell-outputWrapper {
    display: block;
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-notebook-toolbar-padding: 2px 5px 2px 2px;
}

/*-----------------------------------------------------------------------------

/*-----------------------------------------------------------------------------
| Styles
|----------------------------------------------------------------------------*/

.jp-NotebookPanel-toolbar {
  padding: var(--jp-notebook-toolbar-padding);

  /* disable paint containment from lumino 2.0 default strict CSS containment */
  contain: style size !important;
}

.jp-Toolbar-item.jp-Notebook-toolbarCellType .jp-select-wrapper.jp-mod-focused {
  border: none;
  box-shadow: none;
}

.jp-Notebook-toolbarCellTypeDropdown select {
  height: 24px;
  font-size: var(--jp-ui-font-size1);
  line-height: 14px;
  border-radius: 0;
  display: block;
}

.jp-Notebook-toolbarCellTypeDropdown span {
  top: 5px !important;
}

.jp-Toolbar-responsive-popup {
  position: absolute;
  height: fit-content;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-end;
  border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  box-shadow: var(--jp-toolbar-box-shadow);
  background: var(--jp-toolbar-background);
  min-height: var(--jp-toolbar-micro-height);
  padding: var(--jp-notebook-toolbar-padding);
  z-index: 1;
  right: 0;
  top: 0;
}

.jp-Toolbar > .jp-Toolbar-responsive-opener {
  margin-left: auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------

/*-----------------------------------------------------------------------------
| Styles
|----------------------------------------------------------------------------*/

.jp-Notebook-ExecutionIndicator {
  position: relative;
  display: inline-block;
  height: 100%;
  z-index: 9997;
}

.jp-Notebook-ExecutionIndicator-tooltip {
  visibility: hidden;
  height: auto;
  width: max-content;
  width: -moz-max-content;
  background-color: var(--jp-layout-color2);
  color: var(--jp-ui-font-color1);
  text-align: justify;
  border-radius: 6px;
  padding: 0 5px;
  position: fixed;
  display: table;
}

.jp-Notebook-ExecutionIndicator-tooltip.up {
  transform: translateX(-50%) translateY(-100%) translateY(-32px);
}

.jp-Notebook-ExecutionIndicator-tooltip.down {
  transform: translateX(calc(-100% + 16px)) translateY(5px);
}

.jp-Notebook-ExecutionIndicator-tooltip.hidden {
  display: none;
}

.jp-Notebook-ExecutionIndicator:hover .jp-Notebook-ExecutionIndicator-tooltip {
  visibility: visible;
}

.jp-Notebook-ExecutionIndicator span {
  font-size: var(--jp-ui-font-size1);
  font-family: var(--jp-ui-font-family);
  color: var(--jp-ui-font-color1);
  line-height: 24px;
  display: block;
}

.jp-Notebook-ExecutionIndicator-progress-bar {
  display: flex;
  justify-content: center;
  height: 100%;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/*
 * Execution indicator
 */
.jp-tocItem-content::after {
  content: '';

  /* Must be identical to form a circle */
  width: 12px;
  height: 12px;
  background: none;
  border: none;
  position: absolute;
  right: 0;
}

.jp-tocItem-content[data-running='0']::after {
  border-radius: 50%;
  border: var(--jp-border-width) solid var(--jp-inverse-layout-color3);
  background: none;
}

.jp-tocItem-content[data-running='1']::after {
  border-radius: 50%;
  border: var(--jp-border-width) solid var(--jp-inverse-layout-color3);
  background-color: var(--jp-inverse-layout-color3);
}

.jp-tocItem-content[data-running='0'],
.jp-tocItem-content[data-running='1'] {
  margin-right: 12px;
}

/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

.jp-Notebook-footer {
  height: 27px;
  margin-left: calc(
    var(--jp-cell-prompt-width) + var(--jp-cell-collapser-width) +
      var(--jp-cell-padding)
  );
  width: calc(
    100% -
      (
        var(--jp-cell-prompt-width) + var(--jp-cell-collapser-width) +
          var(--jp-cell-padding) + var(--jp-cell-padding)
      )
  );
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  color: var(--jp-ui-font-color3);
  margin-top: 6px;
  background: none;
  cursor: pointer;
}

.jp-Notebook-footer:focus {
  border-color: var(--jp-cell-editor-active-border-color);
}

/* For devices that support hovering, hide footer until hover */
@media (hover: hover) {
  .jp-Notebook-footer {
    opacity: 0;
  }

  .jp-Notebook-footer:focus,
  .jp-Notebook-footer:hover {
    opacity: 1;
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Imports
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| CSS variables
|----------------------------------------------------------------------------*/

:root {
  --jp-side-by-side-output-size: 1fr;
  --jp-side-by-side-resized-cell: var(--jp-side-by-side-output-size);
  --jp-private-notebook-dragImage-width: 304px;
  --jp-private-notebook-dragImage-height: 36px;
  --jp-private-notebook-selected-color: var(--md-blue-400);
  --jp-private-notebook-active-color: var(--md-green-400);
}

/*-----------------------------------------------------------------------------
| Notebook
|----------------------------------------------------------------------------*/

/* stylelint-disable selector-max-class */

.jp-NotebookPanel {
  display: block;
  height: 100%;
}

.jp-NotebookPanel.jp-Document {
  min-width: 240px;
  min-height: 120px;
}

.jp-Notebook {
  padding: var(--jp-notebook-padding);
  outline: none;
  overflow: auto;
  background: var(--jp-layout-color0);
}

.jp-Notebook.jp-mod-scrollPastEnd::after {
  display: block;
  content: '';
  min-height: var(--jp-notebook-scroll-padding);
}

.jp-MainAreaWidget-ContainStrict .jp-Notebook * {
  contain: strict;
}

.jp-Notebook .jp-Cell {
  overflow: visible;
}

.jp-Notebook .jp-Cell .jp-InputPrompt {
  cursor: move;
}

/*-----------------------------------------------------------------------------
| Notebook state related styling
|
| The notebook and cells each have states, here are the possibilities:
|
| - Notebook
|   - Command
|   - Edit
| - Cell
|   - None
|   - Active (only one can be active)
|   - Selected (the cells actions are applied to)
|   - Multiselected (when multiple selected, the cursor)
|   - No outputs
|----------------------------------------------------------------------------*/

/* Command or edit modes */

.jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-InputPrompt {
  opacity: var(--jp-cell-prompt-not-active-opacity);
  color: var(--jp-cell-prompt-not-active-font-color);
}

.jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-OutputPrompt {
  opacity: var(--jp-cell-prompt-not-active-opacity);
  color: var(--jp-cell-prompt-not-active-font-color);
}

/* cell is active */
.jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser {
  background: var(--jp-brand-color1);
}

/* cell is dirty */
.jp-Notebook .jp-Cell.jp-mod-dirty .jp-InputPrompt {
  color: var(--jp-warn-color1);
}

.jp-Notebook .jp-Cell.jp-mod-dirty .jp-InputPrompt::before {
  color: var(--jp-warn-color1);
  content: '•';
}

.jp-Notebook .jp-Cell.jp-mod-active.jp-mod-dirty .jp-Collapser {
  background: var(--jp-warn-color1);
}

/* collapser is hovered */
.jp-Notebook .jp-Cell .jp-Collapser:hover {
  box-shadow: var(--jp-elevation-z2);
  background: var(--jp-brand-color1);
  opacity: var(--jp-cell-collapser-not-active-hover-opacity);
}

/* cell is active and collapser is hovered */
.jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser:hover {
  background: var(--jp-brand-color0);
  opacity: 1;
}

/* Command mode */

.jp-Notebook.jp-mod-commandMode .jp-Cell.jp-mod-selected {
  background: var(--jp-notebook-multiselected-color);
}

.jp-Notebook.jp-mod-commandMode
  .jp-Cell.jp-mod-active.jp-mod-selected:not(.jp-mod-multiSelected) {
  background: transparent;
}

/* Edit mode */

.jp-Notebook.jp-mod-editMode .jp-Cell.jp-mod-active .jp-InputArea-editor {
  border: var(--jp-border-width) solid var(--jp-cell-editor-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
  background-color: var(--jp-cell-editor-active-background);
}

/*-----------------------------------------------------------------------------
| Notebook drag and drop
|----------------------------------------------------------------------------*/

.jp-Notebook-cell.jp-mod-dropSource {
  opacity: 0.5;
}

.jp-Notebook-cell.jp-mod-dropTarget,
.jp-Notebook.jp-mod-commandMode
  .jp-Notebook-cell.jp-mod-active.jp-mod-selected.jp-mod-dropTarget {
  border-top-color: var(--jp-private-notebook-selected-color);
  border-top-style: solid;
  border-top-width: 2px;
}

.jp-dragImage {
  display: block;
  flex-direction: row;
  width: var(--jp-private-notebook-dragImage-width);
  height: var(--jp-private-notebook-dragImage-height);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background);
  overflow: visible;
}

.jp-dragImage-singlePrompt {
  box-shadow: 2px 2px 4px 0 rgba(0, 0, 0, 0.12);
}

.jp-dragImage .jp-dragImage-content {
  flex: 1 1 auto;
  z-index: 2;
  font-size: var(--jp-code-font-size);
  font-family: var(--jp-code-font-family);
  line-height: var(--jp-code-line-height);
  padding: var(--jp-code-padding);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background-color);
  color: var(--jp-content-font-color3);
  text-align: left;
  margin: 4px 4px 4px 0;
}

.jp-dragImage .jp-dragImage-prompt {
  flex: 0 0 auto;
  min-width: 36px;
  color: var(--jp-cell-inprompt-font-color);
  padding: var(--jp-code-padding);
  padding-left: 12px;
  font-family: var(--jp-cell-prompt-font-family);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  line-height: 1.9;
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
}

.jp-dragImage-multipleBack {
  z-index: -1;
  position: absolute;
  height: 32px;
  width: 300px;
  top: 8px;
  left: 8px;
  background: var(--jp-layout-color2);
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  box-shadow: 2px 2px 4px 0 rgba(0, 0, 0, 0.12);
}

/*-----------------------------------------------------------------------------
| Cell toolbar
|----------------------------------------------------------------------------*/

.jp-NotebookTools {
  display: block;
  min-width: var(--jp-sidebar-min-width);
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);

  /* This is needed so that all font sizing of children done in ems is
    * relative to this base size */
  font-size: var(--jp-ui-font-size1);
  overflow: auto;
}

.jp-ActiveCellTool {
  padding: 12px 0;
  display: flex;
}

.jp-ActiveCellTool-Content {
  flex: 1 1 auto;
}

.jp-ActiveCellTool .jp-ActiveCellTool-CellContent {
  background: var(--jp-cell-editor-background);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  border-radius: 0;
  min-height: 29px;
}

.jp-ActiveCellTool .jp-InputPrompt {
  min-width: calc(var(--jp-cell-prompt-width) * 0.75);
}

.jp-ActiveCellTool-CellContent > pre {
  padding: 5px 4px;
  margin: 0;
  white-space: normal;
}

.jp-MetadataEditorTool {
  flex-direction: column;
  padding: 12px 0;
}

.jp-RankedPanel > :not(:first-child) {
  margin-top: 12px;
}

.jp-KeySelector select.jp-mod-styled {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  border: var(--jp-border-width) solid var(--jp-border-color1);
}

.jp-KeySelector label,
.jp-MetadataEditorTool label,
.jp-NumberSetter label {
  line-height: 1.4;
}

.jp-NotebookTools .jp-select-wrapper {
  margin-top: 4px;
  margin-bottom: 0;
}

.jp-NumberSetter input {
  width: 100%;
  margin-top: 4px;
}

.jp-NotebookTools .jp-Collapse {
  margin-top: 16px;
}

/*-----------------------------------------------------------------------------
| Presentation Mode (.jp-mod-presentationMode)
|----------------------------------------------------------------------------*/

.jp-mod-presentationMode .jp-Notebook {
  --jp-content-font-size1: var(--jp-content-presentation-font-size1);
  --jp-code-font-size: var(--jp-code-presentation-font-size);
}

.jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-InputPrompt,
.jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-OutputPrompt {
  flex: 0 0 110px;
}

/*-----------------------------------------------------------------------------
| Side-by-side Mode (.jp-mod-sideBySide)
|----------------------------------------------------------------------------*/
.jp-mod-sideBySide.jp-Notebook .jp-Notebook-cell {
  margin-top: 3em;
  margin-bottom: 3em;
  margin-left: 5%;
  margin-right: 5%;
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell {
  display: grid;
  grid-template-columns: minmax(0, 1fr) min-content minmax(
      0,
      var(--jp-side-by-side-output-size)
    );
  grid-template-rows: auto minmax(0, 1fr) auto;
  grid-template-areas:
    'header header header'
    'input handle output'
    'footer footer footer';
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell.jp-mod-resizedCell {
  grid-template-columns: minmax(0, 1fr) min-content minmax(
      0,
      var(--jp-side-by-side-resized-cell)
    );
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-CellHeader {
  grid-area: header;
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-Cell-inputWrapper {
  grid-area: input;
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-Cell-outputWrapper {
  /* overwrite the default margin (no vertical separation needed in side by side move */
  margin-top: 0;
  grid-area: output;
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-CellFooter {
  grid-area: footer;
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-CellResizeHandle {
  grid-area: handle;
  user-select: none;
  display: block;
  height: 100%;
  cursor: ew-resize;
  padding: 0 var(--jp-cell-padding);
}

.jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-CellResizeHandle::after {
  content: '';
  display: block;
  background: var(--jp-border-color2);
  height: 100%;
  width: 5px;
}

.jp-mod-sideBySide.jp-Notebook
  .jp-CodeCell.jp-mod-resizedCell
  .jp-CellResizeHandle::after {
  background: var(--jp-border-color0);
}

.jp-CellResizeHandle {
  display: none;
}

/*-----------------------------------------------------------------------------
| Placeholder
|----------------------------------------------------------------------------*/

.jp-Cell-Placeholder {
  padding-left: 55px;
}

.jp-Cell-Placeholder-wrapper {
  background: #fff;
  border: 1px solid;
  border-color: #e5e6e9 #dfe0e4 #d0d1d5;
  border-radius: 4px;
  -webkit-border-radius: 4px;
  margin: 10px 15px;
}

.jp-Cell-Placeholder-wrapper-inner {
  padding: 15px;
  position: relative;
}

.jp-Cell-Placeholder-wrapper-body {
  background-repeat: repeat;
  background-size: 50% auto;
}

.jp-Cell-Placeholder-wrapper-body div {
  background: #f6f7f8;
  background-image: -webkit-linear-gradient(
    left,
    #f6f7f8 0%,
    #edeef1 20%,
    #f6f7f8 40%,
    #f6f7f8 100%
  );
  background-repeat: no-repeat;
  background-size: 800px 104px;
  height: 104px;
  position: absolute;
  right: 15px;
  left: 15px;
  top: 15px;
}

div.jp-Cell-Placeholder-h1 {
  top: 20px;
  height: 20px;
  left: 15px;
  width: 150px;
}

div.jp-Cell-Placeholder-h2 {
  left: 15px;
  top: 50px;
  height: 10px;
  width: 100px;
}

div.jp-Cell-Placeholder-content-1,
div.jp-Cell-Placeholder-content-2,
div.jp-Cell-Placeholder-content-3 {
  left: 15px;
  right: 15px;
  height: 10px;
}

div.jp-Cell-Placeholder-content-1 {
  top: 100px;
}

div.jp-Cell-Placeholder-content-2 {
  top: 120px;
}

div.jp-Cell-Placeholder-content-3 {
  top: 140px;
}

</style>
<style type="text/css">
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*
The following CSS variables define the main, public API for styling JupyterLab.
These variables should be used by all plugins wherever possible. In other
words, plugins should not define custom colors, sizes, etc unless absolutely
necessary. This enables users to change the visual theme of JupyterLab
by changing these variables.

Many variables appear in an ordered sequence (0,1,2,3). These sequences
are designed to work well together, so for example, `--jp-border-color1` should
be used with `--jp-layout-color1`. The numbers have the following meanings:

* 0: super-primary, reserved for special emphasis
* 1: primary, most important under normal situations
* 2: secondary, next most important under normal situations
* 3: tertiary, next most important under normal situations

Throughout JupyterLab, we are mostly following principles from Google's
Material Design when selecting colors. We are not, however, following
all of MD as it is not optimized for dense, information rich UIs.
*/

:root {
  /* Elevation
   *
   * We style box-shadows using Material Design's idea of elevation. These particular numbers are taken from here:
   *
   * https://github.com/material-components/material-components-web
   * https://material-components-web.appspot.com/elevation.html
   */

  --jp-shadow-base-lightness: 0;
  --jp-shadow-umbra-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.2
  );
  --jp-shadow-penumbra-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.14
  );
  --jp-shadow-ambient-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.12
  );
  --jp-elevation-z0: none;
  --jp-elevation-z1: 0 2px 1px -1px var(--jp-shadow-umbra-color),
    0 1px 1px 0 var(--jp-shadow-penumbra-color),
    0 1px 3px 0 var(--jp-shadow-ambient-color);
  --jp-elevation-z2: 0 3px 1px -2px var(--jp-shadow-umbra-color),
    0 2px 2px 0 var(--jp-shadow-penumbra-color),
    0 1px 5px 0 var(--jp-shadow-ambient-color);
  --jp-elevation-z4: 0 2px 4px -1px var(--jp-shadow-umbra-color),
    0 4px 5px 0 var(--jp-shadow-penumbra-color),
    0 1px 10px 0 var(--jp-shadow-ambient-color);
  --jp-elevation-z6: 0 3px 5px -1px var(--jp-shadow-umbra-color),
    0 6px 10px 0 var(--jp-shadow-penumbra-color),
    0 1px 18px 0 var(--jp-shadow-ambient-color);
  --jp-elevation-z8: 0 5px 5px -3px var(--jp-shadow-umbra-color),
    0 8px 10px 1px var(--jp-shadow-penumbra-color),
    0 3px 14px 2px var(--jp-shadow-ambient-color);
  --jp-elevation-z12: 0 7px 8px -4px var(--jp-shadow-umbra-color),
    0 12px 17px 2px var(--jp-shadow-penumbra-color),
    0 5px 22px 4px var(--jp-shadow-ambient-color);
  --jp-elevation-z16: 0 8px 10px -5px var(--jp-shadow-umbra-color),
    0 16px 24px 2px var(--jp-shadow-penumbra-color),
    0 6px 30px 5px var(--jp-shadow-ambient-color);
  --jp-elevation-z20: 0 10px 13px -6px var(--jp-shadow-umbra-color),
    0 20px 31px 3px var(--jp-shadow-penumbra-color),
    0 8px 38px 7px var(--jp-shadow-ambient-color);
  --jp-elevation-z24: 0 11px 15px -7px var(--jp-shadow-umbra-color),
    0 24px 38px 3px var(--jp-shadow-penumbra-color),
    0 9px 46px 8px var(--jp-shadow-ambient-color);

  /* Borders
   *
   * The following variables, specify the visual styling of borders in JupyterLab.
   */

  --jp-border-width: 1px;
  --jp-border-color0: var(--md-grey-400);
  --jp-border-color1: var(--md-grey-400);
  --jp-border-color2: var(--md-grey-300);
  --jp-border-color3: var(--md-grey-200);
  --jp-inverse-border-color: var(--md-grey-600);
  --jp-border-radius: 2px;

  /* UI Fonts
   *
   * The UI font CSS variables are used for the typography all of the JupyterLab
   * user interface elements that are not directly user generated content.
   *
   * The font sizing here is done assuming that the body font size of --jp-ui-font-size1
   * is applied to a parent element. When children elements, such as headings, are sized
   * in em all things will be computed relative to that body size.
   */

  --jp-ui-font-scale-factor: 1.2;
  --jp-ui-font-size0: 0.83333em;
  --jp-ui-font-size1: 13px; /* Base font size */
  --jp-ui-font-size2: 1.2em;
  --jp-ui-font-size3: 1.44em;
  --jp-ui-font-family: system-ui, -apple-system, blinkmacsystemfont, 'Segoe UI',
    helvetica, arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
    'Segoe UI Symbol';

  /*
   * Use these font colors against the corresponding main layout colors.
   * In a light theme, these go from dark to light.
   */

  /* Defaults use Material Design specification */
  --jp-ui-font-color0: rgba(0, 0, 0, 1);
  --jp-ui-font-color1: rgba(0, 0, 0, 0.87);
  --jp-ui-font-color2: rgba(0, 0, 0, 0.54);
  --jp-ui-font-color3: rgba(0, 0, 0, 0.38);

  /*
   * Use these against the brand/accent/warn/error colors.
   * These will typically go from light to darker, in both a dark and light theme.
   */

  --jp-ui-inverse-font-color0: rgba(255, 255, 255, 1);
  --jp-ui-inverse-font-color1: rgba(255, 255, 255, 1);
  --jp-ui-inverse-font-color2: rgba(255, 255, 255, 0.7);
  --jp-ui-inverse-font-color3: rgba(255, 255, 255, 0.5);

  /* Content Fonts
   *
   * Content font variables are used for typography of user generated content.
   *
   * The font sizing here is done assuming that the body font size of --jp-content-font-size1
   * is applied to a parent element. When children elements, such as headings, are sized
   * in em all things will be computed relative to that body size.
   */

  --jp-content-line-height: 1.6;
  --jp-content-font-scale-factor: 1.2;
  --jp-content-font-size0: 0.83333em;
  --jp-content-font-size1: 14px; /* Base font size */
  --jp-content-font-size2: 1.2em;
  --jp-content-font-size3: 1.44em;
  --jp-content-font-size4: 1.728em;
  --jp-content-font-size5: 2.0736em;

  /* This gives a magnification of about 125% in presentation mode over normal. */
  --jp-content-presentation-font-size1: 17px;
  --jp-content-heading-line-height: 1;
  --jp-content-heading-margin-top: 1.2em;
  --jp-content-heading-margin-bottom: 0.8em;
  --jp-content-heading-font-weight: 500;

  /* Defaults use Material Design specification */
  --jp-content-font-color0: rgba(0, 0, 0, 1);
  --jp-content-font-color1: rgba(0, 0, 0, 0.87);
  --jp-content-font-color2: rgba(0, 0, 0, 0.54);
  --jp-content-font-color3: rgba(0, 0, 0, 0.38);
  --jp-content-link-color: var(--md-blue-900);
  --jp-content-font-family: system-ui, -apple-system, blinkmacsystemfont,
    'Segoe UI', helvetica, arial, sans-serif, 'Apple Color Emoji',
    'Segoe UI Emoji', 'Segoe UI Symbol';

  /*
   * Code Fonts
   *
   * Code font variables are used for typography of code and other monospaces content.
   */

  --jp-code-font-size: 13px;
  --jp-code-line-height: 1.3077; /* 17px for 13px base */
  --jp-code-padding: 5px; /* 5px for 13px base, codemirror highlighting needs integer px value */
  --jp-code-font-family-default: menlo, consolas, 'DejaVu Sans Mono', monospace;
  --jp-code-font-family: var(--jp-code-font-family-default);

  /* This gives a magnification of about 125% in presentation mode over normal. */
  --jp-code-presentation-font-size: 16px;

  /* may need to tweak cursor width if you change font size */
  --jp-code-cursor-width0: 1.4px;
  --jp-code-cursor-width1: 2px;
  --jp-code-cursor-width2: 4px;

  /* Layout
   *
   * The following are the main layout colors use in JupyterLab. In a light
   * theme these would go from light to dark.
   */

  --jp-layout-color0: white;
  --jp-layout-color1: white;
  --jp-layout-color2: var(--md-grey-200);
  --jp-layout-color3: var(--md-grey-400);
  --jp-layout-color4: var(--md-grey-600);

  /* Inverse Layout
   *
   * The following are the inverse layout colors use in JupyterLab. In a light
   * theme these would go from dark to light.
   */

  --jp-inverse-layout-color0: #111;
  --jp-inverse-layout-color1: var(--md-grey-900);
  --jp-inverse-layout-color2: var(--md-grey-800);
  --jp-inverse-layout-color3: var(--md-grey-700);
  --jp-inverse-layout-color4: var(--md-grey-600);

  /* Brand/accent */

  --jp-brand-color0: var(--md-blue-900);
  --jp-brand-color1: var(--md-blue-700);
  --jp-brand-color2: var(--md-blue-300);
  --jp-brand-color3: var(--md-blue-100);
  --jp-brand-color4: var(--md-blue-50);
  --jp-accent-color0: var(--md-green-900);
  --jp-accent-color1: var(--md-green-700);
  --jp-accent-color2: var(--md-green-300);
  --jp-accent-color3: var(--md-green-100);

  /* State colors (warn, error, success, info) */

  --jp-warn-color0: var(--md-orange-900);
  --jp-warn-color1: var(--md-orange-700);
  --jp-warn-color2: var(--md-orange-300);
  --jp-warn-color3: var(--md-orange-100);
  --jp-error-color0: var(--md-red-900);
  --jp-error-color1: var(--md-red-700);
  --jp-error-color2: var(--md-red-300);
  --jp-error-color3: var(--md-red-100);
  --jp-success-color0: var(--md-green-900);
  --jp-success-color1: var(--md-green-700);
  --jp-success-color2: var(--md-green-300);
  --jp-success-color3: var(--md-green-100);
  --jp-info-color0: var(--md-cyan-900);
  --jp-info-color1: var(--md-cyan-700);
  --jp-info-color2: var(--md-cyan-300);
  --jp-info-color3: var(--md-cyan-100);

  /* Cell specific styles */

  --jp-cell-padding: 5px;
  --jp-cell-collapser-width: 8px;
  --jp-cell-collapser-min-height: 20px;
  --jp-cell-collapser-not-active-hover-opacity: 0.6;
  --jp-cell-editor-background: var(--md-grey-100);
  --jp-cell-editor-border-color: var(--md-grey-300);
  --jp-cell-editor-box-shadow: inset 0 0 2px var(--md-blue-300);
  --jp-cell-editor-active-background: var(--jp-layout-color0);
  --jp-cell-editor-active-border-color: var(--jp-brand-color1);
  --jp-cell-prompt-width: 64px;
  --jp-cell-prompt-font-family: var(--jp-code-font-family-default);
  --jp-cell-prompt-letter-spacing: 0;
  --jp-cell-prompt-opacity: 1;
  --jp-cell-prompt-not-active-opacity: 0.5;
  --jp-cell-prompt-not-active-font-color: var(--md-grey-700);

  /* A custom blend of MD grey and blue 600
   * See https://meyerweb.com/eric/tools/color-blend/#546E7A:1E88E5:5:hex */
  --jp-cell-inprompt-font-color: #307fc1;

  /* A custom blend of MD grey and orange 600
   * https://meyerweb.com/eric/tools/color-blend/#546E7A:F4511E:5:hex */
  --jp-cell-outprompt-font-color: #bf5b3d;

  /* Notebook specific styles */

  --jp-notebook-padding: 10px;
  --jp-notebook-select-background: var(--jp-layout-color1);
  --jp-notebook-multiselected-color: var(--md-blue-50);

  /* The scroll padding is calculated to fill enough space at the bottom of the
  notebook to show one single-line cell (with appropriate padding) at the top
  when the notebook is scrolled all the way to the bottom. We also subtract one
  pixel so that no scrollbar appears if we have just one single-line cell in the
  notebook. This padding is to enable a 'scroll past end' feature in a notebook.
  */
  --jp-notebook-scroll-padding: calc(
    100% - var(--jp-code-font-size) * var(--jp-code-line-height) -
      var(--jp-code-padding) - var(--jp-cell-padding) - 1px
  );

  /* Rendermime styles */

  --jp-rendermime-error-background: #fdd;
  --jp-rendermime-table-row-background: var(--md-grey-100);
  --jp-rendermime-table-row-hover-background: var(--md-light-blue-50);

  /* Dialog specific styles */

  --jp-dialog-background: rgba(0, 0, 0, 0.25);

  /* Console specific styles */

  --jp-console-padding: 10px;

  /* Toolbar specific styles */

  --jp-toolbar-border-color: var(--jp-border-color1);
  --jp-toolbar-micro-height: 8px;
  --jp-toolbar-background: var(--jp-layout-color1);
  --jp-toolbar-box-shadow: 0 0 2px 0 rgba(0, 0, 0, 0.24);
  --jp-toolbar-header-margin: 4px 4px 0 4px;
  --jp-toolbar-active-background: var(--md-grey-300);

  /* Statusbar specific styles */

  --jp-statusbar-height: 24px;

  /* Input field styles */

  --jp-input-box-shadow: inset 0 0 2px var(--md-blue-300);
  --jp-input-active-background: var(--jp-layout-color1);
  --jp-input-hover-background: var(--jp-layout-color1);
  --jp-input-background: var(--md-grey-100);
  --jp-input-border-color: var(--jp-inverse-border-color);
  --jp-input-active-border-color: var(--jp-brand-color1);
  --jp-input-active-box-shadow-color: rgba(19, 124, 189, 0.3);

  /* General editor styles */

  --jp-editor-selected-background: #d9d9d9;
  --jp-editor-selected-focused-background: #d7d4f0;
  --jp-editor-cursor-color: var(--jp-ui-font-color0);

  /* Code mirror specific styles */

  --jp-mirror-editor-keyword-color: #008000;
  --jp-mirror-editor-atom-color: #88f;
  --jp-mirror-editor-number-color: #080;
  --jp-mirror-editor-def-color: #00f;
  --jp-mirror-editor-variable-color: var(--md-grey-900);
  --jp-mirror-editor-variable-2-color: rgb(0, 54, 109);
  --jp-mirror-editor-variable-3-color: #085;
  --jp-mirror-editor-punctuation-color: #05a;
  --jp-mirror-editor-property-color: #05a;
  --jp-mirror-editor-operator-color: #a2f;
  --jp-mirror-editor-comment-color: #408080;
  --jp-mirror-editor-string-color: #ba2121;
  --jp-mirror-editor-string-2-color: #708;
  --jp-mirror-editor-meta-color: #a2f;
  --jp-mirror-editor-qualifier-color: #555;
  --jp-mirror-editor-builtin-color: #008000;
  --jp-mirror-editor-bracket-color: #997;
  --jp-mirror-editor-tag-color: #170;
  --jp-mirror-editor-attribute-color: #00c;
  --jp-mirror-editor-header-color: blue;
  --jp-mirror-editor-quote-color: #090;
  --jp-mirror-editor-link-color: #00c;
  --jp-mirror-editor-error-color: #f00;
  --jp-mirror-editor-hr-color: #999;

  /*
    RTC user specific colors.
    These colors are used for the cursor, username in the editor,
    and the icon of the user.
  */

  --jp-collaborator-color1: #ffad8e;
  --jp-collaborator-color2: #dac83d;
  --jp-collaborator-color3: #72dd76;
  --jp-collaborator-color4: #00e4d0;
  --jp-collaborator-color5: #45d4ff;
  --jp-collaborator-color6: #e2b1ff;
  --jp-collaborator-color7: #ff9de6;

  /* Vega extension styles */

  --jp-vega-background: white;

  /* Sidebar-related styles */

  --jp-sidebar-min-width: 250px;

  /* Search-related styles */

  --jp-search-toggle-off-opacity: 0.5;
  --jp-search-toggle-hover-opacity: 0.8;
  --jp-search-toggle-on-opacity: 1;
  --jp-search-selected-match-background-color: rgb(245, 200, 0);
  --jp-search-selected-match-color: black;
  --jp-search-unselected-match-background-color: var(
    --jp-inverse-layout-color0
  );
  --jp-search-unselected-match-color: var(--jp-ui-inverse-font-color0);

  /* Icon colors that work well with light or dark backgrounds */
  --jp-icon-contrast-color0: var(--md-purple-600);
  --jp-icon-contrast-color1: var(--md-green-600);
  --jp-icon-contrast-color2: var(--md-pink-600);
  --jp-icon-contrast-color3: var(--md-blue-600);

  /* Button colors */
  --jp-accept-color-normal: var(--md-blue-700);
  --jp-accept-color-hover: var(--md-blue-800);
  --jp-accept-color-active: var(--md-blue-900);
  --jp-warn-color-normal: var(--md-red-700);
  --jp-warn-color-hover: var(--md-red-800);
  --jp-warn-color-active: var(--md-red-900);
  --jp-reject-color-normal: var(--md-grey-600);
  --jp-reject-color-hover: var(--md-grey-700);
  --jp-reject-color-active: var(--md-grey-800);

  /* File or activity icons and switch semantic variables */
  --jp-jupyter-icon-color: #f37626;
  --jp-notebook-icon-color: #f37626;
  --jp-json-icon-color: var(--md-orange-700);
  --jp-console-icon-background-color: var(--md-blue-700);
  --jp-console-icon-color: white;
  --jp-terminal-icon-background-color: var(--md-grey-800);
  --jp-terminal-icon-color: var(--md-grey-200);
  --jp-text-editor-icon-color: var(--md-grey-700);
  --jp-inspector-icon-color: var(--md-grey-700);
  --jp-switch-color: var(--md-grey-400);
  --jp-switch-true-position-color: var(--md-orange-900);
}
</style>
<style type="text/css">
/* Force rendering true colors when outputing to pdf */
* {
  -webkit-print-color-adjust: exact;
}

/* Misc */
a.anchor-link {
  display: none;
}

/* Input area styling */
.jp-InputArea {
  overflow: hidden;
}

.jp-InputArea-editor {
  overflow: hidden;
}

.cm-editor.cm-s-jupyter .highlight pre {
/* weird, but --jp-code-padding defined to be 5px but 4px horizontal padding is hardcoded for pre.cm-line */
  padding: var(--jp-code-padding) 4px;
  margin: 0;

  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
  color: inherit;

}

.jp-OutputArea-output pre {
  line-height: inherit;
  font-family: inherit;
}

.jp-RenderedText pre {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-code-font-size);
}

/* Hiding the collapser by default */
.jp-Collapser {
  display: none;
}

@page {
    margin: 0.5in; /* Margin for each printed piece of paper */
}

@media print {
  .jp-Cell-inputWrapper,
  .jp-Cell-outputWrapper {
    display: block;
  }
}
</style>
<!-- Load mathjax -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/latest.js?config=TeX-AMS_CHTML-full,Safe"> </script>
<!-- MathJax configuration -->
<script type="text/x-mathjax-config">
    init_mathjax = function() {
        if (window.MathJax) {
        // MathJax loaded
            MathJax.Hub.Config({
                TeX: {
                    equationNumbers: {
                    autoNumber: "AMS",
                    useLabelIds: true
                    }
                },
                tex2jax: {
                    inlineMath: [ ['$','$'], ["\\(","\\)"] ],
                    displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
                    processEscapes: true,
                    processEnvironments: true
                },
                displayAlign: 'center',
                CommonHTML: {
                    linebreaks: {
                    automatic: true
                    }
                }
            });

            MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
        }
    }
    init_mathjax();
    </script>
<!-- End of mathjax configuration --><script type="module">
  document.addEventListener("DOMContentLoaded", async () => {
    const diagrams = document.querySelectorAll(".jp-Mermaid > pre.mermaid");
    // do not load mermaidjs if not needed
    if (!diagrams.length) {
      return;
    }
    const mermaid = (await import("https://cdnjs.cloudflare.com/ajax/libs/mermaid/10.7.0/mermaid.esm.min.mjs")).default;
    const parser = new DOMParser();

    mermaid.initialize({
      maxTextSize: 100000,
      maxEdges: 100000,
      startOnLoad: false,
      fontFamily: window
        .getComputedStyle(document.body)
        .getPropertyValue("--jp-ui-font-family"),
      theme: document.querySelector("body[data-jp-theme-light='true']")
        ? "default"
        : "dark",
    });

    let _nextMermaidId = 0;

    function makeMermaidImage(svg) {
      const img = document.createElement("img");
      const doc = parser.parseFromString(svg, "image/svg+xml");
      const svgEl = doc.querySelector("svg");
      const { maxWidth } = svgEl?.style || {};
      const firstTitle = doc.querySelector("title");
      const firstDesc = doc.querySelector("desc");

      img.setAttribute("src", `data:image/svg+xml,${encodeURIComponent(svg)}`);
      if (maxWidth) {
        img.width = parseInt(maxWidth);
      }
      if (firstTitle) {
        img.setAttribute("alt", firstTitle.textContent);
      }
      if (firstDesc) {
        const caption = document.createElement("figcaption");
        caption.className = "sr-only";
        caption.textContent = firstDesc.textContent;
        return [img, caption];
      }
      return [img];
    }

    async function makeMermaidError(text) {
      let errorMessage = "";
      try {
        await mermaid.parse(text);
      } catch (err) {
        errorMessage = `${err}`;
      }

      const result = document.createElement("details");
      result.className = 'jp-RenderedMermaid-Details';
      const summary = document.createElement("summary");
      summary.className = 'jp-RenderedMermaid-Summary';
      const pre = document.createElement("pre");
      const code = document.createElement("code");
      code.innerText = text;
      pre.appendChild(code);
      summary.appendChild(pre);
      result.appendChild(summary);

      const warning = document.createElement("pre");
      warning.innerText = errorMessage;
      result.appendChild(warning);
      return [result];
    }

    async function renderOneMarmaid(src) {
      const id = `jp-mermaid-${_nextMermaidId++}`;
      const parent = src.parentNode;
      let raw = src.textContent.trim();
      const el = document.createElement("div");
      el.style.visibility = "hidden";
      document.body.appendChild(el);
      let results = null;
      let output = null;
      try {
        let { svg } = await mermaid.render(id, raw, el);
        svg = cleanMermaidSvg(svg);
        results = makeMermaidImage(svg);
        output = document.createElement("figure");
        results.map(output.appendChild, output);
      } catch (err) {
        parent.classList.add("jp-mod-warning");
        results = await makeMermaidError(raw);
        output = results[0];
      } finally {
        el.remove();
      }
      parent.classList.add("jp-RenderedMermaid");
      parent.appendChild(output);
    }


    /**
     * Post-process to ensure mermaid diagrams contain only valid SVG and XHTML.
     */
    function cleanMermaidSvg(svg) {
      return svg.replace(RE_VOID_ELEMENT, replaceVoidElement);
    }


    /**
     * A regular expression for all void elements, which may include attributes and
     * a slash.
     *
     * @see https://developer.mozilla.org/en-US/docs/Glossary/Void_element
     *
     * Of these, only `<br>` is generated by Mermaid in place of `\n`,
     * but _any_ "malformed" tag will break the SVG rendering entirely.
     */
    const RE_VOID_ELEMENT =
      /<\s*(area|base|br|col|embed|hr|img|input|link|meta|param|source|track|wbr)\s*([^>]*?)\s*>/gi;

    /**
     * Ensure a void element is closed with a slash, preserving any attributes.
     */
    function replaceVoidElement(match, tag, rest) {
      rest = rest.trim();
      if (!rest.endsWith('/')) {
        rest = `${rest} /`;
      }
      return `<${tag} ${rest}>`;
    }

    void Promise.all([...diagrams].map(renderOneMarmaid));
  });
</script>
<style>
  .jp-Mermaid:not(.jp-RenderedMermaid) {
    display: none;
  }

  .jp-RenderedMermaid {
    overflow: auto;
    display: flex;
  }

  .jp-RenderedMermaid.jp-mod-warning {
    width: auto;
    padding: 0.5em;
    margin-top: 0.5em;
    border: var(--jp-border-width) solid var(--jp-warn-color2);
    border-radius: var(--jp-border-radius);
    color: var(--jp-ui-font-color1);
    font-size: var(--jp-ui-font-size1);
    white-space: pre-wrap;
    word-wrap: break-word;
  }

  .jp-RenderedMermaid figure {
    margin: 0;
    overflow: auto;
    max-width: 100%;
  }

  .jp-RenderedMermaid img {
    max-width: 100%;
  }

  .jp-RenderedMermaid-Details > pre {
    margin-top: 1em;
  }

  .jp-RenderedMermaid-Summary {
    color: var(--jp-warn-color2);
  }

  .jp-RenderedMermaid:not(.jp-mod-warning) pre {
    display: none;
  }

  .jp-RenderedMermaid-Summary > pre {
    display: inline-block;
    white-space: normal;
  }
</style>
<!-- End of mermaid configuration --></head>
<body class="jp-Notebook" data-jp-theme-light="true" data-jp-theme-name="JupyterLab Light">
<main>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=0092cce7-ac8a-4236-b35b-0ee06c6ceb52">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h2 id="CO2-Emissions">CO2 Emissions<a class="anchor-link" href="#CO2-Emissions">¶</a></h2><h3 id="Reading-data">Reading data<a class="anchor-link" href="#Reading-data">¶</a></h3>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs" id="cell-id=b1cb4fc0-acf0-4201-a2ef-c6ce5688ae31">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [115]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">from</span> <span class="nn">matplotlib</span> <span class="kn">import</span> <span class="n">pyplot</span> <span class="k">as</span> <span class="n">plt</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs" id="cell-id=7ea5575e-fc13-4939-bc09-ef6af45bb054">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [116]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">"FuelConsumption.csv"</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=65020f4d-e082-443a-862f-6304456507ff">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [117]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[117]:</div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html" tabindex="0">
<div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>MODELYEAR</th>
<th>ENGINESIZE</th>
<th>CYLINDERS</th>
<th>FUELCONSUMPTION_CITY</th>
<th>FUELCONSUMPTION_HWY</th>
<th>FUELCONSUMPTION_COMB</th>
<th>FUELCONSUMPTION_COMB_MPG</th>
<th>CO2EMISSIONS</th>
</tr>
</thead>
<tbody>
<tr>
<th>count</th>
<td>1067.0</td>
<td>1067.000000</td>
<td>1067.000000</td>
<td>1067.000000</td>
<td>1067.000000</td>
<td>1067.000000</td>
<td>1067.000000</td>
<td>1067.000000</td>
</tr>
<tr>
<th>mean</th>
<td>2014.0</td>
<td>3.346298</td>
<td>5.794752</td>
<td>13.296532</td>
<td>9.474602</td>
<td>11.580881</td>
<td>26.441425</td>
<td>256.228679</td>
</tr>
<tr>
<th>std</th>
<td>0.0</td>
<td>1.415895</td>
<td>1.797447</td>
<td>4.101253</td>
<td>2.794510</td>
<td>3.485595</td>
<td>7.468702</td>
<td>63.372304</td>
</tr>
<tr>
<th>min</th>
<td>2014.0</td>
<td>1.000000</td>
<td>3.000000</td>
<td>4.600000</td>
<td>4.900000</td>
<td>4.700000</td>
<td>11.000000</td>
<td>108.000000</td>
</tr>
<tr>
<th>25%</th>
<td>2014.0</td>
<td>2.000000</td>
<td>4.000000</td>
<td>10.250000</td>
<td>7.500000</td>
<td>9.000000</td>
<td>21.000000</td>
<td>207.000000</td>
</tr>
<tr>
<th>50%</th>
<td>2014.0</td>
<td>3.400000</td>
<td>6.000000</td>
<td>12.600000</td>
<td>8.800000</td>
<td>10.900000</td>
<td>26.000000</td>
<td>251.000000</td>
</tr>
<tr>
<th>75%</th>
<td>2014.0</td>
<td>4.300000</td>
<td>8.000000</td>
<td>15.550000</td>
<td>10.850000</td>
<td>13.350000</td>
<td>31.000000</td>
<td>294.000000</td>
</tr>
<tr>
<th>max</th>
<td>2014.0</td>
<td>8.400000</td>
<td>12.000000</td>
<td>30.200000</td>
<td>20.500000</td>
<td>25.800000</td>
<td>60.000000</td>
<td>488.000000</td>
</tr>
</tbody>
</table>
</div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=842ee76e-e7f8-4f09-8e60-ef43dec26d5d">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [118]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="p">[[</span><span class="s2">"ENGINESIZE"</span><span class="p">,</span> <span class="s2">"CYLINDERS"</span><span class="p">,</span> <span class="s2">"FUELCONSUMPTION_COMB"</span><span class="p">,</span> <span class="s2">"CO2EMISSIONS"</span><span class="p">]]</span>
<span class="n">df</span><span class="o">.</span><span class="n">hist</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[118]:</div>
<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain" tabindex="0">
<pre>array([[&lt;Axes: title={'center': 'ENGINESIZE'}&gt;,
        &lt;Axes: title={'center': 'CYLINDERS'}&gt;],
       [&lt;Axes: title={'center': 'FUELCONSUMPTION_COMB'}&gt;,
        &lt;Axes: title={'center': 'CO2EMISSIONS'}&gt;]], dtype=object)</pre>
</div>
</div>
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedImage jp-OutputArea-output" tabindex="0">
<img alt="No description has been provided for this image" class="" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAjEAAAGzCAYAAADe/0a6AAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjkuMiwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8hTgPZAAAACXBIWXMAAA9hAAAPYQGoP6dpAABmlklEQVR4nO3de1wU9f4/8NdyW64LonI7CuIl77e8sZmXFEEj07TylqKZFgc9ImXqUQG1DopWahGWmVhJnvCbesQroWIqoqLmrUhN01KwMkEhlgU+vz/87eS6y31hGXg9H4996H7mszPvz+zM7JvPzHxGIYQQICIiIpIZC3MHQERERFQVTGKIiIhIlpjEEBERkSwxiSEiIiJZYhJDREREssQkhoiIiGSJSQwRERHJEpMYIiIikiUmMURERCRLTGKIiIhIlpjEyEB8fDwUCkWpr2PHjgGA9P6dd94pdR4nT540mHb27FlMmTIFvr6+sLW1haOjI7p164Y333wTP/30k17dyZMnw9HRUa9s4MCBUCgUGD58uMG8r127BoVCgZUrV0plBw8eLLM9mzdvluoWFhZi9erV6N69O1QqFVxcXNCxY0dMnz4dP/zwQ6nt0y23vFd8fHyF6i9btqy8r4moXrly5QpeffVVtGzZEra2tlCpVOjbty9Wr16N6OhoKBQK7N271+hnn376aTg7O+PmzZsAHhybZsyYUebyBg4ciE6dOumVtWjRAgqFAjNnzjSorzuObNmyRSp79Fhpa2sLLy8vBAYGYs2aNbh3757BfKKiosrc97OysgAYHiMsLCzg6uqKYcOGIS0tzWibDh8+jGHDhuEf//gHbG1t4e3tjeHDhyMhIaHMdUEVZ2XuAKjilixZAl9fX4Py1q1b671fsWIFQkJCYG9vX+48161bh5CQEDRp0gQTJkxAu3btUFRUhPPnz+Ozzz7DqlWr8Ndff8HS0rLceSUlJSEjIwM9evSoUHv+9a9/oVevXgblarVa+v/o0aOxe/dujBs3DtOmTYNWq8UPP/yApKQkPPHEE2jXrp3ReTdt2hSff/650WnFxcUIDw/H/fv30b17d71p48aNw9NPP23wmUfrEdVnO3fuxAsvvAClUolJkyahU6dOKCwsxOHDhzFnzhxMmDABnTt3xj//+U+cP38ednZ20mcTExOxe/duxMbGwsvLyyTxrFu3DvPnz6/w/HTHSq1Wi6ysLBw8eBBhYWF499138b///Q9dunQx+ExcXJzBH2gA4OLiovded4woLi7Gjz/+iA8//BBPPfUUTpw4gc6dO0v1EhMTMWbMGHTr1g2zZs1Co0aNcPXqVRw6dAjr1q3D+PHjK7cSyDhBdd6GDRsEAHHixIky6wEQ3bp1EwDEO++8U+48jhw5IiwtLUX//v1Fbm6uwfz++usvsXDhQlFUVCSVBQcHCwcHB716AwYMEN7e3qJRo0Zi+PDhetOuXr0qAIgVK1ZIZQcOHBAARGJiYpntOX78uAAg3n77bYNpRUVF4vfffy+zfaVZsGCBwToyFidRQ/TTTz8JR0dH0a5dO3Hz5k2D6ZcuXRKrVq0SaWlpwsLCQsyfP1+alpubK7y8vISfn58oLi6WygGI0NDQMpc7YMAA0bFjR70yHx8f0bFjR2FlZSVmzpypN83YcaSs40BKSoqws7MTPj4+Ij8/XyqPjIwUAMRvv/1WZnylHSN2794tAIiQkBC98g4dOoiOHTsKjUZjMK/s7Owyl0UVx9NJ9Uzfvn0xaNAgxMTE4K+//iqz7uLFi6FQKLBp0yY4OTkZTLe1tcXSpUsr1Avj5OSE2bNnY8eOHTh16lSV43/YlStXADxo06MsLS3RuHHjSs8zJSUF0dHRePrppzF79uxqx0hU38TExOD+/ftYv349PD09Daa3bt0as2bNgp+fH1577TWsXLkSFy9eBAAsXLgQt2/fxscffwwLC9P8vLRo0QKTJk3CunXrpNNTVTFo0CAsWrQIP//8M7744guTxAYA/fr1A/D38UrnypUr6NWrF2xsbAw+4+bmZrLlN3RMYmQkJycHv//+u97rjz/+MKgXFRWF7OxsxMXFlTqv/Px87N+/HwMHDkSzZs1MEp+uyzQqKqpC9e/du2fQnt9//x1CCACAj48PAGDTpk0oKiqqdnzZ2dmYMGECPDw8sHHjRigUCoM6+fn5RmMyxfKJ5GDHjh1o2bIlnnjiiXLrRkdHo2nTpnj11VeRkZGB2NhYvPHGG3qnVUxhwYIFKCoqqva1aRMnTgQA7Nu3z2DanTt3DPb7u3fvljvPa9euAQAaNWqkV+7j44OUlBT88ssv1YqZysYkRkb8/f3RtGlTvdc//vEPg3r9+vXDU089hRUrVpTaG3P58mUUFRUZXEgHGO7MhYWFFYpPpVIhLCyswr0xL7/8skF7mjZtiuzsbACAn58fBgwYgHXr1qFZs2YYP348PvzwQ1y/fr1C8TyspKQEEydOxG+//YZNmzahSZMmRutFRkYajcnYBdFE9U1ubi5+/fXXCichKpUKa9asweHDhxEQEAAfHx9ERESYPK6WLVti4sSJWLduHW7dulXl+TRr1gzOzs4GvSYA0LZtW4P93s/Pz6Ce7g+d7OxsHD58GFOmTAEAPP/883r15s6dixs3bqBVq1YYNGgQIiIicPjwYZSUlFQ5fjLEC3tlJDY2Fo899pheWWmneqKiojBgwACsXbvW6GmT3NxcADB6IVvLli2Rk5MjvU9MTDTYQUsza9YsrFq1CosXL8b27dvLrBsRESF1xT7M1dUVAKS7H1auXIkvvvgCX375Jb788kuEhobixRdfxEcffWRw0V1pli1bhuTkZCxatAgDBw4std706dPxwgsvGJR36NChQsshkjPdccHY6eXSjB49Gk8//TR27dqFTZs26V3ka0oLFy7E559/jmXLlmH16tVVno+jo6PRu5T+7//+DyqVSq/MwcHBoF5kZCQiIyP15vfOO+8YHCNffvll/OMf/8C7776LAwcO4MCBA1i6dClatmyJzz//vEI9XVQ+JjEy0rt3b/Ts2bNCdfv374+nnnoKMTExeO211wym6w5S9+/fN5i2fft2aLVafPfdd3jjjTcqFaOzszPCwsIQGRmJ06dPG3SxPqxz587w9/cvc35KpRILFizAggULcOvWLaSmpmL16tX46quvYG1tXaFz20eOHEFkZCT69eund/Axpk2bNuXGRFRf6X7Ejf3Il6VXr17YtWtXhY9PVaHrjfn4448xb968Ks/n/v37Rq9J6d+/f6k9tA/T/aFTUFCA/fv3Y82aNSguLjZaNzAwEIGBgcjPz0dGRgb++9//Yu3atXjmmWfwww8/8NoYE+DppHosMjISWVlZ+OijjwymtW7dGlZWVjh//rzBtAEDBsDf37/Ct0o/atasWXBxccHixYur9PnSeHp6YuzYsTh06BDatGmDr776qtxrVe7cuYNx48ZBpVIhISGhQhcpEzVUKpUKXl5eRo8LdYHu2pjly5dX6fO//PILcnJyDIalqAzdHzrPPPMM3n33XcyePRvz5s0r85Szvb09+vXrhw8++AALFy7En3/+id27d1c5Bvobk5h6bMCAARg4cCCWL19ucG2Mg4MDBg4ciNTUVPz6668mXa6uN2b79u04ffq0SecNANbW1ujSpQu0Wi1+//33MutOnjwZN27cwIYNG0x2ATNRffbMM8/gypUrpQ7gZk6tWrXCSy+9hI8++qhK18boxo4KDAw0WUwLFiyAk5MTFi5cWKH6ut6q6lzbQ39jElPPRUVFISsrCx9//LHBtIiICBQXF+Oll14yelpJd5dQVYSFhcHFxQVLliyp8jwuXbpk9CLeu3fvIi0tDY0aNULTpk1L/fyqVauwY8cOzJw5E88++2yV4yBqSN588004ODjglVdekS6yf9iVK1eqdU1KdS1cuBBarRYxMTGV+tz+/fuxdOlS+Pr6YsKECSaLx8XFBa+++ir27t2LM2fOSOUpKSlG6+/atQvAgwuJqfp4TYyM7N69W2+ofZ0nnngCLVu2NPqZAQMGYMCAAUhNTTWYpuvenDlzJtq0aSON2FtYWIgff/wRmzZtgo2NDTw8PCodq7OzM2bNmlXmKaVvv/0WBQUFBuVdunRBly5d8N1332H8+PEYNmwY+vXrB1dXV/z666/YuHEjbt68iVWrVpV6eujs2bOYO3cuHB0d0bVr11KvndEtS+fUqVNG67Zq1UpvJGGi+qpVq1ZISEjAmDFj0L59e70Re48ePYrExERMnjy50vM9efIk3nrrLYPygQMH4sknn6xUfC+99BI2btxYah3dsbKoqAjZ2dnYv38/kpOT4ePjg//973+wtbU1+MyWLVuM3ugwZMgQuLu7lxmT7oaGZcuWSY9NGTFiBHx9fTF8+HC0atUKeXl5+Oabb7Bjxw706tXL6GNaqArMPdoelU83CmVprw0bNgghSh8VUzeyJUoZyfL06dNi0qRJwtvbW9jY2AgHBwfRpUsX8frrr4vLly/r1S1txN5HR9oUQog///xTODs7lzpib2mvyMhIIcSDUS2XLVsmBgwYIDw9PYWVlZVo1KiRGDRokNiyZYvRdaRrX3nr7NFl6UbjLO0VHBxc5ndEVN/8+OOPYtq0aaJFixbCxsZGODk5ib59+4r3339fFBQU6NUtb9TbsvatpUuXCiFKH7E3KCjIYH6XLl0SlpaWpY7Yq3vZ2NgIDw8PMWTIELF69WqjI5PrYi/tdeDAASFE+aN6T548WVhaWkrHzC+//FKMHTtWtGrVStjZ2QlbW1vRoUMHsWDBAqNxUNUohKjGOQMiIiIiM+E1MURERCRLTGKIiIhIlpjEEBERkSwxiSEiIiJZYhJDREREssQkhoiIiGRJloPdlZSU4ObNm3BycoJCoTB3OET1ihAC9+7dg5eXFywsGt7fOTy+ENUcUx9fZJnE3Lx5E82bNzd3GET12o0bNxrk86Z4fCGqeaY6vsgyiXFycgLwYCXoHh1vTlqtFvv27UNAQACsra3NHY5JsE3yUBNtys3NRfPmzaX9rKEx9/FFbtupnOKVU6yAvOKtaKymPr7IMonRdfGqVKo6k8TY29tDpVLV+Q2totgmeajJNjXUUynmPr7IbTuVU7xyihWQV7yVjdVUx5eGd8KbiIiI6gUmMURERCRLTGKIiIhIlpjEEBERkSzJ8sJec2oxb6dBmdJSIKY30ClqLzTFFb9Y6dqyIFOGRkQy12LeziofTx7F4ws1BOyJISIiIlliEkNERESyxCSGiIiIZIlJDBHVScuWLYNCoUBYWJhUVlBQgNDQUDRu3BiOjo4YPXo0srOz9T53/fp1BAUFwd7eHm5ubpgzZw6KiopqOXoiqg1MYoiozjlx4gQ++ugjdOnSRa989uzZ2LFjBxITE5GamoqbN29i1KhR0vTi4mIEBQWhsLAQR48excaNGxEfH4+IiIjabgIR1QImMURUp9y/fx8TJkzAunXr0KhRI6k8JycH69evx7vvvotBgwahR48e2LBhA44ePYpjx44BAPbt24eLFy/iiy++QLdu3TBs2DAsXboUsbGxKCwsNFeTiKiG8BZrIqpTQkNDERQUBH9/f7z11ltSeUZGBrRaLfz9/aWydu3awdvbG2lpafDz80NaWho6d+4Md3d3qU5gYCBCQkJw4cIFdO/e3WB5Go0GGo1Gep+bmwvgwbNgtFptTTSxVEpLAaWFePD///9vVdVW7Lrl1Pa6qgo5xQrIK96KxmrqtjCJIaI6Y/PmzTh16hROnDhhMC0rKws2NjZwcXHRK3d3d0dWVpZU5+EERjddN82Y6OhoLF682KB83759sLe3r0ozqiym99//X9qzpFrz2rVrVzWjqZzk5ORaXV51yClWQF7xlhdrfn6+SZfHJKYeMTYQX1VdWhpgsnkRVcSNGzcwa9YsJCcnw9bWttaWO3/+fISHh0vvc3Nz0bx5cwQEBNT6U6w7Re2F0kJgac8SLDppAU1J1Qe7Ox8VaMLISqfVapGcnIwhQ4bI4knLcokVkFe8FY1V19NpKkxiiKhOyMjIwO3bt/H4449LZcXFxTh06BA++OAD7N27F4WFhbh7965eb0x2djY8PDwAAB4eHjh+/LjefHV3L+nqPEqpVEKpVBqUW1tb1/oPx8Mj9GpKFNUasbe2YzfH+qoqOcUKyCve8mI1dTt4YS8R1QmDBw/GuXPncObMGenVs2dPTJgwQfq/tbU1UlJSpM9kZmbi+vXrUKvVAAC1Wo1z587h9u3bUp3k5GSoVCp06NCh1ttERDWLPTFEVCc4OTmhU6dOemUODg5o3LixVD516lSEh4fD1dUVKpUKM2fOhFqthp+fHwAgICAAHTp0wMSJExETE4OsrCwsXLgQoaGhRntbiEjemMQQkWy89957sLCwwOjRo6HRaBAYGIgPP/xQmm5paYmkpCSEhIRArVbDwcEBwcHBWLJkiRmjJqKawiSGiOqsgwcP6r23tbVFbGwsYmNjS/2Mj49Prd+ZQ0TmwWtiiIiISJaYxBAREZEsMYkhIiIiWWISQ0RERLLEJIaIiIhkiUkMERERyRKTGCIiIpIlJjFEREQkS0xiiIiISJY4Yi8REZWrxbydRsuVlgIxvYFOUXsr9dTta8uCTBUaNWDsiSEiIiJZYhJDREREssQkhoiIiGSJSQwRERHJEpMYIiIikiUmMURERCRLlUpioqOj0atXLzg5OcHNzQ0jR45EZmamXp2CggKEhoaicePGcHR0xOjRo5Gdna1X5/r16wgKCoK9vT3c3NwwZ84cFBUVVb81RERE1GBUKolJTU1FaGgojh07huTkZGi1WgQEBCAvL0+qM3v2bOzYsQOJiYlITU3FzZs3MWrUKGl6cXExgoKCUFhYiKNHj2Ljxo2Ij49HRESE6VpFRERE9V6lBrvbs2eP3vv4+Hi4ubkhIyMD/fv3R05ODtavX4+EhAQMGjQIALBhwwa0b98ex44dg5+fH/bt24eLFy/im2++gbu7O7p164alS5di7ty5iIqKgo2NjelaR0RERPVWtUbszcnJAQC4uroCADIyMqDVauHv7y/VadeuHby9vZGWlgY/Pz+kpaWhc+fOcHd3l+oEBgYiJCQEFy5cQPfu3Q2Wo9FooNFopPe5ubkAAK1WC61WW50mVJrSUhiWWQi9fyvK1LEbi62qdLHV9vqtSWxT5eZJRFTXVTmJKSkpQVhYGPr27YtOnToBALKysmBjYwMXFxe9uu7u7sjKypLqPJzA6KbrphkTHR2NxYsXG5Tv27cP9vb2VW1ClcT0Ln3a0p4llZrXrl27qhmNvrJiq6zk5GS9f+sTtqls+fn5JpsXEVFNqnISExoaivPnz+Pw4cOmjMeo+fPnIzw8XHqfm5uL5s2bIyAgACqVqsaX/7BOUXsNypQWAkt7lmDRSQtoSir+7JDzUYGmDM1obFV1esEgJCcnY8iQIbC2tjbZfM1Jq9WyTRWg6+kkIqrrqpTEzJgxA0lJSTh06BCaNWsmlXt4eKCwsBB3797V643Jzs6Gh4eHVOf48eN689PdvaSr8yilUgmlUmlQbm1tXes/RmU94ExToqjUA9BMHXtlll0eXWzmWMc1jW0qf15ERHJQqbuThBCYMWMGtm7div3798PX11dveo8ePWBtbY2UlBSpLDMzE9evX4darQYAqNVqnDt3Drdv35bqJCcnQ6VSoUOHDtVpCxERETUgleqJCQ0NRUJCArZv3w4nJyfpGhZnZ2fY2dnB2dkZU6dORXh4OFxdXaFSqTBz5kyo1Wr4+fkBAAICAtChQwdMnDgRMTExyMrKwsKFCxEaGmq0t4WIiIjImEr1xMTFxSEnJwcDBw6Ep6en9Prvf/8r1XnvvffwzDPPYPTo0ejfvz88PDzw9ddfS9MtLS2RlJQES0tLqNVqvPTSS5g0aRKWLFliulYRkSzFxcWhS5cuUKlUUKlUUKvV2L17tzSdg2kS0cMq1RMjRPm38Nra2iI2NhaxsbGl1vHx8TH5nTlEJH/NmjXDsmXL0KZNGwghsHHjRowYMQKnT59Gx44dMXv2bOzcuROJiYlwdnbGjBkzMGrUKBw5cgTA34Npenh44OjRo7h16xYmTZoEa2tr/Oc//zFz64jI1Ko1TgwRkSkNHz5c7/3bb7+NuLg4HDt2DM2aNeNgmkSkh0kMEdVJxcXFSExMRF5eHtRqdYMZTLOqg2c+qrYG06wrg31WZplyGdBRTvFWNFZTt4VJDBHVKefOnYNarUZBQQEcHR2xdetWdOjQAWfOnGlQg2lWdvDMR9X2YJrmHuyzMuQ24KWc4i0vVlMPpskkhojqlLZt2+LMmTPIycnBli1bEBwcjNTU1BpbXl0bTLOqg2c+qrYG06wrg31WhNwGvJRTvBWN1dSDaTKJIaI6xcbGBq1btwbwYOypEydOYPXq1RgzZkyDGkyzsoNnPqq2B9M092CflSG3AS/lFG95sZq6HZW6xZqIqLaVlJRAo9FwME0iMsCeGCKqM+bPn49hw4bB29sb9+7dQ0JCAg4ePIi9e/dyME0iMsAkhojqjNu3b2PSpEm4desWnJ2d0aVLF+zduxdDhgwB8GAwTQsLC4wePRoajQaBgYH48MMPpc/rBtMMCQmBWq2Gg4MDgoODOZgmUT3FJIaI6oz169eXOZ2DaRLRw3hNDBEREckSkxgiIiKSJSYxREREJEtMYoiIiEiWmMQQERGRLDGJISIiIlliEkNERESyxCSGiIiIZIlJDBEREckSkxgiIiKSJSYxREREJEt8dhIREclai3k7K1RPaSkQ0xvoFLUXmmJFqfWuLQsyVWhUw9gTQ0RERLLEnhgzquhfD0RERGSIPTFEREQkS0xiiIiISJaYxBAREZEsMYkhIiIiWWISQ0RERLLEJIaIiIhkiUkMERERyRKTGCIiIpIlJjFEREQkS0xiiIiISJaYxBAREZEsMYkhIiIiWeIDIKlWmPphl9eWBZl0fmR+0dHR+Prrr/HDDz/Azs4OTzzxBJYvX462bdtKdQoKCvD6669j8+bN0Gg0CAwMxIcffgh3d3epzvXr1xESEoIDBw7A0dERwcHBiI6OhpUVD3dE9Q17YoioTkhNTUVoaCiOHTuG5ORkaLVaBAQEIC8vT6oze/Zs7NixA4mJiUhNTcXNmzcxatQoaXpxcTGCgoJQWFiIo0ePYuPGjYiPj0dERIQ5mkRENYx/mhBRnbBnzx699/Hx8XBzc0NGRgb69++PnJwcrF+/HgkJCRg0aBAAYMOGDWjfvj2OHTsGPz8/7Nu3DxcvXsQ333wDd3d3dOvWDUuXLsXcuXMRFRUFGxsbg+VqNBpoNBrpfW5uLgBAq9VCq9XWYIsNKS0FlBbiwf///79VZerYlZbG46lqvKaMr7TYDOpVMNba/t5Lo4ujrsRTlorGauq2MIkhojopJycHAODq6goAyMjIgFarhb+/v1SnXbt28Pb2RlpaGvz8/JCWlobOnTvrnV4KDAxESEgILly4gO7duxssJzo6GosXLzYo37dvH+zt7U3drDLF9P77/0t7llRrXrt27apmNPoejs2YysZryvjKi+1R5cVq6nVXXcnJyeYOocLKizU/P9+ky2MSQ0R1TklJCcLCwtC3b1906tQJAJCVlQUbGxu4uLjo1XV3d0dWVpZU5+EERjddN82Y+fPnIzw8XHqfm5uL5s2bIyAgACqVylRNqpBOUXuhtBBY2rMEi05aQFOiqPK8zkcFmjCyB7EZU9V4TRlfabE9qqKxmnrdVZVWq0VycjKGDBkCa2trc4dTporGquvpNBUmMURU54SGhuL8+fM4fPhwjS9LqVRCqVQalFtbW9f6D4em+O8fVk2JQu99ZZk69vJiqWy8poyvsuupvFjrWsJgjm2xqsqL1dTt4IW9RFSnzJgxA0lJSThw4ACaNWsmlXt4eKCwsBB3797Vq5+dnQ0PDw+pTnZ2tsF03TQiql+YxBBRnSCEwIwZM7B161bs378fvr6+etN79OgBa2trpKSkSGWZmZm4fv061Go1AECtVuPcuXO4ffu2VCc5ORkqlQodOnSonYYQUa2p96eTTD0+CRHVjNDQUCQkJGD79u1wcnKSrmFxdnaGnZ0dnJ2dMXXqVISHh8PV1RUqlQozZ86EWq2Gn58fACAgIAAdOnTAxIkTERMTg6ysLCxcuBChoaFGTxkRkbzV+ySGiOQhLi4OADBw4EC98g0bNmDy5MkAgPfeew8WFhYYPXq03mB3OpaWlkhKSkJISAjUajUcHBwQHByMJUuW1FYziKgWMYkhojpBiPLH+rC1tUVsbCxiY2NLrePj41PnbpEloprBa2KIiIhIlpjEEBERkSxVOok5dOgQhg8fDi8vLygUCmzbtk1vuhACERER8PT0hJ2dHfz9/XHp0iW9Onfu3MGECROgUqng4uKCqVOn4v79+9VqCBERETUslU5i8vLy0LVr11LPScfExGDNmjVYu3Yt0tPT4eDggMDAQBQUFEh1JkyYgAsXLiA5ORlJSUk4dOgQpk+fXvVWEBERUYNT6Qt7hw0bhmHDhhmdJoTAqlWrsHDhQowYMQIA8Nlnn8Hd3R3btm3D2LFj8f3332PPnj04ceIEevbsCQB4//338fTTT2PlypXw8vKqRnOIiIiooTDp3UlXr15FVlaW3gPanJ2d0adPH6SlpWHs2LFIS0uDi4uLlMAAgL+/PywsLJCeno7nnnvOYL7VecpsRZ9uWh2meupsXWLqp6ea+nuoSlxyeiJsRdVEm+rT+iGi+s2kSYxucCpjD2B7+AFtbm5u+kFYWcHV1bXUB7RV5ymzlX26aXVU96mzdYnuSaSmenqqqb+H6txCK6cnwlaUKdtk6qfMEhHVFFmME1Odp8xW9Omm1WGqp87WJacXDDLp01NN/T1U5SmzcnoibEXVRJtM/ZRZIqKaYtIkRveAtezsbHh6ekrl2dnZ6Natm1Tn4eeaAEBRURHu3LlT6gPaqvOU2eo8BbayqvvU2bpEt15N9fRUU6+X6sQkpyfCVpQp21Tf1g0R1V8mHSfG19cXHh4eeg9oy83NRXp6ut4D2u7evYuMjAypzv79+1FSUoI+ffqYMhwiIiKqxyrdE3P//n1cvnxZen/16lWcOXMGrq6u8Pb2RlhYGN566y20adMGvr6+WLRoEby8vDBy5EgAQPv27TF06FBMmzYNa9euhVarxYwZMzB27FjemUREREQVVukk5uTJk3jqqaek97prVYKDgxEfH48333wTeXl5mD59Ou7evYsnn3wSe/bsga2trfSZTZs2YcaMGRg8eLD0MLc1a9aYoDlERETUUFQ6iRk4cGCZD2pTKBRYsmRJmU+NdXV1RUJCQmUXTURERCThs5OIiIhIlpjEEBERkSwxiSEiIiJZYhJDREREssQkhoiIiGSJSQwRERHJEpMYIiIikiUmMURERCRLTGKIiIhIlpjEEBERkSwxiSEiIiJZYhJDREREslTpB0BSw9Apai9iej/4V1OsMHc41EAcOnQIK1asQEZGBm7duoWtW7di5MiR0nQhBCIjI7Fu3TrcvXsXffv2RVxcHNq0aSPVuXPnDmbOnIkdO3bAwsICo0ePxurVq+Ho6GiGFhFRTWJPDBHVGXl5eejatStiY2ONTo+JicGaNWuwdu1apKenw8HBAYGBgSgoKJDqTJgwARcuXEBycjKSkpJw6NAhTJ8+vbaaQES1iD0xRFRnDBs2DMOGDTM6TQiBVatWYeHChRgxYgQA4LPPPoO7uzu2bduGsWPH4vvvv8eePXtw4sQJ9OzZEwDw/vvv4+mnn8bKlSvh5eVVa20hoprHJIaIZOHq1avIysqCv7+/VObs7Iw+ffogLS0NY8eORVpaGlxcXKQEBgD8/f1hYWGB9PR0PPfccwbz1Wg00Gg00vvc3FwAgFarhVarrcEWGVJaCigtxIP///9/q8rUsSstjcdT1XhNGV9psRnUq2Cstf29l0YXR12JpywVjdXUbWESQ0SykJWVBQBwd3fXK3d3d5emZWVlwc3NTW+6lZUVXF1dpTqPio6OxuLFiw3K9+3bB3t7e1OEXmExvf/+/9KeJdWa165du6oZjb6HYzOmsvGaMr7yYntUebGaet1VV3JysrlDqLDyYs3Pzzfp8pjEEFGDNn/+fISHh0vvc3Nz0bx5cwQEBEClUtVqLJ2i9kJpIbC0ZwkWnbSApqTqF9Wfjwo0YWQPYjOmqvGaMr7SYntURWM19bqrKq1Wi+TkZAwZMgTW1tbmDqdMFY1V19NpKkxiiEgWPDw8AADZ2dnw9PSUyrOzs9GtWzepzu3bt/U+V1RUhDt37kiff5RSqYRSqTQot7a2rvUfjofvBNSUKKp1Z6CpYy8vlsrGa8r4Krueyou1riUM5tgWq6q8WE3dDt6dRESy4OvrCw8PD6SkpEhlubm5SE9Ph1qtBgCo1WrcvXsXGRkZUp39+/ejpKQEffr0qfWYiahmsSeGZKnFvJ2V/ozSUhgd++basiBThkbVcP/+fVy+fFl6f/XqVZw5cwaurq7w9vZGWFgY3nrrLbRp0wa+vr5YtGgRvLy8pLFk2rdvj6FDh2LatGlYu3YttFotZsyYgbFjx/LOJKJ6iEkMEdUZJ0+exFNPPSW9112rEhwcjPj4eLz55pvIy8vD9OnTcffuXTz55JPYs2cPbG1tpc9s2rQJM2bMwODBg6XB7tasWVPrbSGimsckhojqjIEDB0KI0m9/VSgUWLJkCZYsWVJqHVdXVyQkJNREeERUx/CaGCIiIpIl9sRQg1eV62vKwmtsiIhqB3tiiIiISJaYxBAREZEsMYkhIiIiWWISQ0RERLLEJIaIiIhkiUkMERERyRKTGCIiIpIlJjFEREQkS0xiiIiISJaYxBAREZEsMYkhIiIiWWISQ0RERLLEJIaIiIhkiUkMERERyRKTGCIiIpIlJjFEREQkS0xiiIiISJaYxBAREZEsMYkhIiIiWWISQ0RERLLEJIaIiIhkycrcARAREZF5tJi30yTzUVoKxPQ2yawqhT0xREREJEtMYoiIiEiWzHo6KTY2FitWrEBWVha6du2K999/H717m6E/iojqnYZ+fDHVaQKqnup8D7pTNJ2i9kJTrAAAXFsWZKrQ6gWz9cT897//RXh4OCIjI3Hq1Cl07doVgYGBuH37trlCIqJ6gscXoobBbD0x7777LqZNm4YpU6YAANauXYudO3fi008/xbx58/TqajQaaDQa6X1OTg4A4M6dO9BqtWUux6ooz8SRG1lGiUB+fgmstBYoLlHU+PJqA9tUdX/88YfJ5tUnOqXM6UoLgYXdS9BtwdfQVKBN6fMHl1vn3r17AAAhRMWCrINq6/hS3vdTWVaQ375X1XhNuZ9U9Dhf0VjNEZvRzxqJ15SxAab7jdTF+scff8Da2rrUeiY/vggz0Gg0wtLSUmzdulWvfNKkSeLZZ581qB8ZGSkA8MUXX7X4unHjRi0dEUyLxxe++Kr7L1MdX8zSE/P777+juLgY7u7ueuXu7u744YcfDOrPnz8f4eHh0vuSkhLcuXMHjRs3hkJh/r9UcnNz0bx5c9y4cQMqlcrc4ZgE2yQPNdEmIQTu3bsHLy8vk8yvtsn9+CK37VRO8copVkBe8VY0VlMfX2QxToxSqYRSqdQrc3FxMU8wZVCpVHV+Q6sstkkeTN0mZ2dnk82rrqurxxe5badyildOsQLyircisZry+GKWC3ubNGkCS0tLZGdn65VnZ2fDw8PDHCERUT3B4wtRw2GWJMbGxgY9evRASsrfF8WVlJQgJSUFarXaHCERUT3B4wtRw2G200nh4eEIDg5Gz5490bt3b6xatQp5eXnS3QRyolQqERkZadAlLWdskzzUxzaZgpyPL3L7TuUUr5xiBeQVr7liVQhhvvsoP/jgA2kwqm7dumHNmjXo06ePucIhonqExxei+s+sSQwRERFRVfHZSURERCRLTGKIiIhIlpjEEBERkSwxiSEiIiJZYhJTDdHR0ejVqxecnJzg5uaGkSNHIjMz09xhmdSyZcugUCgQFhZm7lCq5ddff8VLL72Exo0bw87ODp07d8bJkyfNHVaVFRcXY9GiRfD19YWdnR1atWqFpUuXyvqhjfQ3Oex3ctqn6vL+cujQIQwfPhxeXl5QKBTYtm2b3nQhBCIiIuDp6Qk7Ozv4+/vj0qVL5gkWZcer1Woxd+5cdO7cGQ4ODvDy8sKkSZNw8+bNGouHSUw1pKamIjQ0FMeOHUNycjK0Wi0CAgKQl1fzT86uDSdOnMBHH32ELl26mDuUavnzzz/Rt29fWFtbY/fu3bh48SLeeecdNGrUyNyhVdny5csRFxeHDz74AN9//z2WL1+OmJgYvP/+++YOjapJDvud3Papury/5OXloWvXroiNjTU6PSYmBmvWrMHatWuRnp4OBwcHBAYGoqCgoJYjfaCsePPz83Hq1CksWrQIp06dwtdff43MzEw8++yzNReQSR4jSUIIIW7fvi0AiNTUVHOHUm337t0Tbdq0EcnJyWLAgAFi1qxZ5g6pyubOnSuefPJJc4dhUkFBQeLll1/WKxs1apSYMGGCmSIiU5DLfie3fUou+wsAvaevl5SUCA8PD7FixQqp7O7du0KpVIovv/zSDBHqezReY44fPy4AiJ9//rlGYmBPjAnl5OQAAFxdXc0cSfWFhoYiKCgI/v7+5g6l2v73v/+hZ8+eeOGFF+Dm5obu3btj3bp15g6rWp544gmkpKTgxx9/BAB89913OHz4MIYNG2bmyKg65LLfyW2fkuv+cvXqVWRlZeltD87OzujTpw/S0tLMGFnF5eTkQKFQ1NhDVWXxFGs5KCkpQVhYGPr27YtOnTqZO5xq2bx5M06dOoUTJ06YOxST+OmnnxAXF4fw8HD8+9//xokTJ/Cvf/0LNjY2CA4ONnd4VTJv3jzk5uaiXbt2sLS0RHFxMd5++21MmDDB3KFRFclpv5PbPiXX/SUrKwsA4O7urlfu7u4uTavLCgoKMHfuXIwbN67GnsLNJMZEQkNDcf78eRw+fNjcoVTLjRs3MGvWLCQnJ8PW1tbc4ZhESUkJevbsif/85z8AgO7du+P8+fNYu3ZtnTzgVsRXX32FTZs2ISEhAR07dsSZM2cQFhYGLy8v2bapIZPbfie3fYr7S+3TarV48cUXIYRAXFxczS2oRk5SNTChoaGiWbNm4qeffjJ3KNW2detWAUBYWlpKLwBCoVAIS0tLUVRUZO4QK83b21tMnTpVr+zDDz8UXl5eZoqo+po1ayY++OADvbKlS5eKtm3bmikiqg657Xdy26fksr/gkWtMrly5IgCI06dP69Xr37+/+Ne//lW7wRnxaLw6hYWFYuTIkaJLly7i999/r9EY2BNTDUIIzJw5E1u3bsXBgwfh6+tr7pCqbfDgwTh37pxe2ZQpU9CuXTvMnTsXlpaWZoqs6vr27Wtw6/uPP/4IHx8fM0VUffn5+bCw0L+kzdLSEiUlJWaKiKpDbvud3PYpue4vvr6+8PDwQEpKCrp16wYAyM3NRXp6OkJCQswbXCl0PTCXLl3CgQMH0Lhx4xpdHpOYaggNDUVCQgK2b98OJycn6Ryls7Mz7OzszBxd1Tg5ORlc0+Pg4IDGjRvL9lqf2bNn44knnsB//vMfvPjiizh+/Dg+/vhjfPzxx+YOrcqGDx+Ot99+G97e3ujYsSNOnz6Nd999Fy+//LK5Q6MqkNt+J7d9qi7vL/fv38fly5el91evXsWZM2fg6uoKb29vhIWF4a233kKbNm3g6+uLRYsWwcvLCyNHjqxz8Xp6euL555/HqVOnkJSUhOLiYul30dXVFTY2NqYPqEb7eeo5AEZfGzZsMHdoJlWXb/WsqB07dohOnToJpVIp2rVrJz7++GNzh1Qtubm5YtasWcLb21vY2tqKli1bigULFgiNRmPu0MhE6vp+J6d9qi7vLwcOHDD6OxIcHCyEeHCb9aJFi4S7u7tQKpVi8ODBIjMzs07Ge/Xq1VJ/Fw8cOFAj8SiEqANDFhIRERFVEseJISIiIlliEkNERESyxCSGiIiIZIlJDBEREckSkxgiIiKSJVklMfHx8VAoFEZf8+bNAwAoFArMmDHD6Oe3bNkChUKBgwcPSmWTJ08udZ4PD/998OBBKBQKbNmypdw4CwoK8N5776FPnz5wdnaGra0tHnvsMcyYMUN6ANnDjhw5gueeew7u7u5QKpVo0aIFXn31VVy/ft2gblRUFBQKBdzd3ZGfn28wvUWLFnjmmWf0yu7fv4/IyEh06tRJGnuiW7dumDVrFm7evKm3LhwdHUttl6OjIyZPnmywThQKBb744gujn+nbty8UCoXBWBctWrTQW9dubm7o168ftm7dCqDs7/rhV4sWLfTWy++//24QQ1JSEoYOHYrGjRtL38Ubb7yBP/74w6Cubnvo0qULjN24V9b2VZ6tW7di2LBhaNKkCWxsbODl5YUXX3wR+/fvN6h7/fp1vPbaa2jRogWUSiXc3NwwcuRIHDlyxKCuKb8HW1tbtGnTBnPmzMGdO3eq1E6qG65cuYJXX30VLVu2hK2tLVQqFfr27YvVq1fjr7/+kupptVqsWbMGvXr1gpOTExwdHdGrVy+sWbMGWq1Wb575+fmIjY1FQEAAPD094eTkhO7duyMuLg7FxcV6dR/eLo29Nm/eLNXVbYelPfhy3bp10udOnjwplZe23+/YsQMDBgyAm5sb7O3t0bJlS7z44ovYs2ePXr3ffvsNs2bNQrt27WBnZwc3Nzf07t0bc+fOxf3796V6pR0bhRD4/PPP0b9/f7i4uMDe3h6dO3fGkiVLkJeXZ1B/4MCBUCgUGD58uMG0a9euQaFQYOXKlQblU6ZMQatWrWBrawsPDw/0798fkZGRRtdVQyPLwe6WLFliMDpudQaEUiqV+OSTTwzKqzJK5u+//46hQ4ciIyMDzzzzDMaPHw9HR0dkZmZi8+bN+Pjjj1FYWCjVf//99zFr1iy0bNkSM2fOhKenJ77//nt88skn+O9//4tdu3bhiSeeMFjO7du3ERcXh9dff73MeLRaLfr3748ffvgBwcHBmDlzJu7fv48LFy4gISEBzz33HLy8vCrdzofZ2toiISEBL730kl75tWvXcPTo0VKfBdOtWzcp/ps3b+Kjjz7CqFGjEBcXh4CAAHz++ed69V955RX07t0b06dPl8rKSroA4I033sA777yDrl27Yu7cuXB1dcWpU6fwwQcfYPPmzUhJSUHbtm0NPnfu3Dl8/fXXGD16dIXWQVmEEHj55ZcRHx+P7t27Izw8HB4eHrh16xa2bt2KwYMH48iRI9L3fOTIETz99NNSmzt06ICsrCzEx8ejX79+WL16NWbOnGmwHFN8DwUFBcjIyMCqVauQmpqK48ePV7v9VPt27tyJF154AUqlEpMmTUKnTp1QWFiIw4cPY86cObhw4QI+/vhj5OXlISgoCKmpqXjmmWcwefJkWFhYYM+ePZg1axa+/vpr7Ny5Ew4ODgAePPhx5syZGDx4MMLDw6FSqbB3717885//xLFjx7Bx40aDWP71r3+hV69eBuVqtVrvva2tLQ4cOICsrCx4eHjoTdu0aRNsbW1RUFBQbttXrlyJOXPmYMCAAZg/fz7s7e1x+fJlfPPNN9i8eTOGDh0KALhz5w569uyJ3NxcvPzyy2jXrh3++OMPnD17FnFxcQgJCSnz+FJcXIzx48fjq6++Qr9+/RAVFQV7e3t8++23WLx4MRITE/HNN98YPLwRePCHVUZGBnr06FFmWy5fvoxevXrBzs4OL7/8Mlq0aIFbt27h1KlTWL58ORYvXlzu+qj3amT0mRqyYcMGAUCcOHGi1DoARGhoqNFpiYmJBoPuBAcHCwcHh3KXrRvgJzExscx6QUFBwsLCQmzZssVgWkFBgXj99del94cPHxYWFhaiX79+Ii8vT6/u5cuXhbu7u/D09BR37tyRyiMjIwUA0a1bN+Hu7i7y8/P1Pufj4yOCgoKk91999ZUAIDZt2mQQz19//SVycnKk9+WtCwcHB2kAJiH+XiejRo0SVlZW4rffftOr//bbbwt3d3fx5JNPio4dO5YZpxBC3Lp1Szg4OIjHHnusQst/mG69PBxDQkKCACDGjBlj8OyZ9PR0YW9vLzp37iy0Wq3eOrCzsxOPPfaY6NKliygpKdH7XFnbV2lWrFghAIiwsDCD+QkhxGeffSbS09OFEELcuXNHeHh4CHd3d3H58mW9evn5+aJfv37CwsJCHDlyRCo39fcghBBvvPGGACB+/PHHSrWVzO+nn34Sjo6Ool27duLmzZsG0y9duiRWrVolhBBi+vTpAoB4//33Dep98MEHAoB47bXXpLLffvtNnD9/3qDulClTBABx6dIlqayix0whHmyHgwcPFiqVSopN58aNG8LCwkKMHj3a4Pj/6H6v1WqFSqUSQ4YMMbqc7Oxs6f8xMTECgN6+pJOTkyP++usv6b2xY+N//vMfAUC88cYbBp//3//+JywsLMTQoUP1ygcMGCC8vb1Fo0aNxPDhw/Wm6QaKW7FihVT2z3/+U1hZWYlr166V2ZaGTFank+q69PR07Ny5E1OnTjX6F7xSqdTrKly6dCkUCgU2btwIe3t7vbqtWrVCTEwMbt26hY8++shgXhEREcjOzi736aBXrlwB8OB0wqN0XczVNWLECCiVSiQmJuqVJyQk4MUXX6xwj5aHhwfat2+Pq1evVjsmAFi8eDEaNWqEjz/+2CAGXZfxuXPnDE4RWlhYYOHChTh79qx0equq/vrrL0RHR6Ndu3ZYuXIlFAqFQZ2JEyeid+/eAICPPvoIWVlZWLFiBVq1aqVXz87ODhs3boRCocCSJUsM5mOq7wGA9JewlZUsO2sbtJiYGNy/fx/r16+Hp6enwfTWrVtj1qxZ+OWXX7B+/XoMGjTI6CnS0NBQPPXUU/jkk0/wyy+/AACaNGmCjh07GtR97rnnAADff/99leO2tbXFqFGjkJCQoFf+5ZdfolGjRggMDCx3Hr///jtyc3ONHu8AwM3NTfr/lStXYGlpCT8/P4N6KpWqzKeJ//XXX1ixYgUee+wxREdHG0wfPnw4goODsWfPHhw7dkxvmpOTE2bPno0dO3bg1KlTZbbnypUraNasmdFnUj3cloZMlklMTk4Ofv/9d71XdT06P93OUBn/+9//ADz4USpPfn4+UlJS0K9fv1IfHDlmzBgolUokJSUZTOvXrx8GDRqEmJgYvfPbj9Jt/J999pnRazxMwd7eHiNGjMCXX34plX333Xe4cOECxo8fX+H5aLVa3LhxwyQPDLt06RIyMzMxYsSIUhO1SZMmAYDR9Tt+/Hi0adMGS5YsqdZ6O3z4MO7cuYPx48dXKInYsWMHbG1t8eKLLxqd7uvriyeffBL79+83+N6r+j1otVppm//ll1+wY8cOvPvuu+jfv3+9eKhpQ7Njxw60bNnS6Gnoh+3evRvFxcXSfmDMpEmTUFRUZHAtyaN0z8dp0qSJwbR79+4ZPb4a26/Gjx+P48ePS398AQ+S8Oeffx7W1tZlxgA8+GG3s7PDjh07yr2my8fHB8XFxQanrSvi8OHD+PPPPzF+/PhSE/2yji+zZs1Co0aNEBUVVW6MN27cMHrdHD0gyyTG398fTZs21XtVR15ensH8mjZtWuoPSWl0f4V07ty53LqXLl1CUVERunbtWmodpVKJtm3blvrXTWRkJLKzs7F27dpS5zFy5Ei0bdsWERER8PX1xZQpU/Dpp5/i9u3b5cZYGePHj8fhw4dx48YNAA/OYbds2dLoXzk6D/94nj17FpMmTUJ2djZeeOGFasdz8eJFAChz/bZo0QIqlcro+rW0tMTChQvx3XffYdu2bVWOozLbBPAg7rZt20KpVJZap2vXrtBqtXoPYdOpyvewb98+aZtv3rw5nn32Wfj6+uLrr7+uUMxUd+Tm5uLXX3+t0PZWkX1EN62sHpbCwkKsWrUKvr6+Rq99efnll40eX7Ozsw3qDho0CB4eHlIi/v333+PMmTMV/mPIwsICc+bMQUZGBry9vfH000/jP//5j9EeD11ckydPRvv27RESEoIvv/wSOTk55S6nuutOpVIhLCys3N6Yf/3rX7CxscHgwYPRvXt3hIWFYfv27UZv6mioZJnExMbGIjk5We9VHba2tgbzS05OxrJlyyo1H13PjZOTU7l17927V6G6Tk5OpfYI9e/fH0899VSZvTF2dnZIT0/HnDlzADy462fq1Knw9PTEzJkzodFoyo21IgICAuDq6orNmzdDCIHNmzdj3LhxZX7m4R/Prl27IjExERMnTsTy5curHY8p1u+ECROq3RtTmW0CeBB3RWJ+eN4Pq8r30KdPH2mbT0pKwttvv40LFy7g2WefLbOXj+oeUx+DytrWdGbMmIGLFy/igw8+MNorERERYfT46urqalDX0tISL774opTEbNq0Cc2bN0e/fv3KbY/O4sWLkZCQgO7du2Pv3r1YsGABevTogccff1wvoXB3d8d3332H1157DX/++SfWrl2L8ePHw83NDUuXLi1znzfFutP1xpR1cW7Hjh1x5swZvPTSS7h27RpWr16NkSNHwt3dHevWrStzPTQUsjzh3bt3b/Ts2bPKn3/0ugRLS8tSb+2rDN1pi3v37sHFxaXMuroNXLczlKa8H7WoqCgMGDAAa9euxezZs43WcXZ2RkxMDGJiYvDzzz8jJSUFK1euxAcffABnZ2e89dZbZcbwMGPXdACAtbU1XnjhBSQkJKB37964ceNGuX899enTB2+99RYUCgXs7e3Rvn37ctdbRVVm/ZZ2blnXGxMcHIxt27ZJ5/0r4+FtoiKcnJwqFLOu7qOq8j00adJEb/sPCgpC27Zt8fzzz+OTTz4xeicU1U2V2d4qso+U92O9YsUKrFu3DkuXLpXuqHtU586dK3V8HT9+PNasWYPvvvsOCQkJGDt2bKnHndKMGzcO48aNQ25uLtLT0xEfH4+EhAQMHz4c58+fl6538fT0RFxcHD788ENcunQJe/fuxfLlyxEREQFPT0+88sorRudvinXn7OyMsLAwREZG4vTp02jUqJHReo899hg+//xzFBcX4+LFi0hKSkJMTAymT58OX19fk/x2yZkse2LKolQqS/3rUdcFV9YFW9XRrl07AA9uzy1P69atYWVlhbNnz5ZaR6PRIDMzEx06dCi1Tv/+/TFw4MByr43R8fHxwcsvv4wjR47AxcUFmzZtkqbZ2tpCo9EY/QtECIGCgoIy19348eNx5swZREVFoWvXrmXGDfz94zl48GCo1WqTJTAA0L59ewAoc/3+/PPPyM3NLTPOCRMmoHXr1lXujanMNgE8iDszM7PMHrKzZ8/C2toabdq0MTq9st+DMYMHDwYAHDp0qNKfJfNRqVTw8vLC+fPny61bkX1EN83YNhQfH4+5c+fitddew8KFC6sYsaE+ffqgVatWCAsLw9WrVyt1Xd2jVCoVhgwZgk2bNiE4OBhXrlxBenq6QT2FQoHHHnsMM2fOxKFDh2BhYaF3bHxUddedzqxZs+Di4lKhW6UtLS3RuXNnzJ8/X7rhoKwYG4p6l8T4+PggMzPT6DRdubErvU1BN4BRaQOOPczBwQFPPfUUDh06hJ9//tlona+++goajcZg8LpHRUVFISsry+hdTKVp1KgRWrVqhVu3bkllPj4+KCoq0ruoTufy5csoLi4uc909+eST8Pb2xsGDB6t14DGFxx57DI899hi2bdtW6l9Ln332GQCUuX51vTFnzpzB9u3bKx3Hk08+iUaNGuHLL780GAzMmGeeeQYFBQUGdxjpXLt2Dd9++y0GDRoEOzu7UpdZ3e+hqKgIAPQG/CJ5eOaZZ3DlyhWkpaWVWW/YsGGwtLQs88LWzz77DFZWVtLYKjrbt2/HK6+8glGjRiE2NtYkcT9s3LhxOHjwINq3b49u3bqZZJ663vuHj3nGtGzZEo0aNSqz3pNPPgkXFxckJCSUul9X5Pii643Zvn07Tp8+XV4TJBVtS0NQ75KYp59+GseOHUNGRoZe+d27d7Fp0yZ069bNYCAlU1Gr1Rg6dCg++eQToxeDFhYW4o033pDeL1y4EEIITJ482aAX5erVq3jzzTfh6emJV199tczlDhgwAAMHDsTy5csNBoP67rvvjN699fPPP0sXkeoMGzYMAPDBBx8Y1NcdqHR1jFEoFFizZg0iIyMrdIdWTYuIiMCff/6J1157zeBAk5GRgeXLl6NTp07lDmj30ksvoXXr1lUaWMre3h5z587F999/j7lz5xrtzfniiy+kQeVeffVVuLm5Yc6cOfjpp5/06hUUFGDKlCkQQiAiIqLUZZrie9ixYweAsi9cpLrpzTffhIODA1555RWjF89euXIFq1evRvPmzTFlyhR88803RodqWLt2Lfbv34+pU6eiWbNmUvmhQ4cwduxY9O/fH5s2bYKFhel/Rl555RVERkbinXfeqdTn8vPzS03edu/eDQDSMS89Pd3oqLrHjx/HH3/8YXQQTB17e3u88cYbyMzMxIIFCwym79y5E/Hx8QgMDCzzonoACAsLg4uLi9FhE7799luDUZMBYNeuXXptachkeU1MWebNm4fExET0798fr776Ktq1a4ebN28iPj4et27dwoYNGww+U1RUVGrvyXPPPSeNVgkA//d//4cffvjBoF5wcDCaN2+Ozz77DAEBARg1ahSGDx+OwYMHw8HBAZcuXcLmzZtx69YtaayY/v37Y+XKlQgPD0eXLl0wefJkeHp64ocffsC6detQUlKCXbt2lXqu9GGRkZF46qmnDMqTk5MRGRmJZ599Fn5+fnB0dMRPP/2ETz/9FBqNRu8Wv27duuGVV17B6tWrcenSJQwZMkSax65du/DKK6+U+6M2YsQIjBgxotx4a8OECRNw4sQJrF69GhcvXsSECRPQqFEjnDp1Cp9++ikaN26MLVu2lHvrpqWlJRYsWIApU6ZUKQ7dCKnvvPMODhw4gOeffx4eHh7IysrCtm3bcPz4cRw9ehQApJiCgoLw+OOPG4zYe/nyZaxevbrc22cr8z38+uuv0vZfWFiI7777Dh999BGaNGnC62FkqFWrVkhISMCYMWPQvn17vRF7jx49isTEROnxIe+99x5++OEH/POf/8SePXukHpe9e/di+/btGDBggF4i8fPPP+PZZ5+FQqHA888/b9Bj2KVLF3Tp0kWv7NtvvzU60q6xujo+Pj7l3n5sTH5+Pp544gn4+flh6NChaN68Oe7evYtt27bh22+/xciRI9G9e3cAwOeff45NmzbhueeeQ48ePWBjY4Pvv/8en376KWxtbfHvf/+7zGXNmzcPp0+fxvLly5GWlobRo0fDzs4Ohw8fxhdffIH27dsbHcH4Uc7Ozpg1a5bRP5KWL1+OjIwMjBo1SlpXp06dwmeffQZXV1eEhYVVeh3VO2YZYq+KKjJirxBC/PLLL+KVV14R//jHP4SVlZVwdXUVzzzzjDh27JhB3eDgYAGg1NfVq1eFEH+PPlna69tvv5XmmZ+fL1auXCl69eolHB0dhY2NjWjTpo2YOXOmwSisQghx6NAhMWLECNGkSRNhbW0tvL29xbRp04yO0mhsZFqdAQMGCAB6I7D+9NNPIiIiQvj5+Qk3NzdhZWUlmjZtKoKCgsT+/fsN5lFcXCxWr14tunbtKmxtbYWtra3o2rWrWLNmjSguLtarW9EROQcMGFDhkWLLUtkRe3W2bdsmhgwZIho1aiSUSqVo3bq1eP31143WLW3UYq1WK1q1alWlEXt1tmzZIgICAoSrq6uwsrISnp6eYsyYMeLgwYMGda9evSqmTZsmvL29hbW1tWjSpIl49tln9bYznep+Dw9vxxYWFsLNzU2MGzfO6LZK8vHjjz+KadOmiRYtWggbGxvh5OQk+vbtK95//31RUFAg1dNoNOK9994TPXr0EA4ODsLe3l48/vjjYtWqVaKwsFBvnuUdByMjI6tUtyLHA2PHf2Mj9q5bt06MHDlS+Pj4CKVSKezt7UX37t3FihUrhEajkT579uxZMWfOHPH444/r7ZMvvPCCOHXqlN6ySzsuFBcXiw0bNoi+ffsKlUolbG1tRceOHcXixYvF/fv3Deob2weFEOLPP/8Uzs7OBiP2HjlyRISGhopOnToJZ2dn6fdh8uTJ4sqVK2Wur4ZCIUQNjYBGREREVIPq3TUxRERE1DDUu2tiiGrLb7/9VuYdRzY2NkYH9CIiItPg6SSiKmrRokWpt8cDD+4aO3jwYO0FRETUwLAnhqiKNm3aVOYAgxW5q4yIiKqOPTFEREQkS7ywl4iIiGRJlqeTSkpKcPPmTTg5OVX6wWBEVDYhBO7duwcvL68aGY21ruPxhajmmPr4Issk5ubNm2jevLm5wyCq127cuKE33HxDweMLUc0z1fFFlkmM7tHmN27ckB49Xx6tVot9+/YhICCg3GHm6xK5xg3IN3a5xg2YJvbc3Fw0b95c2s8amtKOL3LeLoypT+2pT20B6ld7Hm2LqY8vlUpi4uLiEBcXh2vXrgEAOnbsiIiICOmhgAUFBXj99dexefNmaDQaBAYG4sMPP4S7u7s0j+vXryMkJAQHDhyAo6MjgoODER0dDSurioei6+JVqVSVSmLs7e2hUqlktVHINW5AvrHLNW7AtLE31FMppR1f5LxdGFOf2lOf2gLUr/aU1hZTHV8qdUKqWbNmWLZsGTIyMnDy5EkMGjQII0aMwIULFwAAs2fPxo4dO5CYmIjU1FTcvHkTo0aNkj5fXFyMoKAg6UFkGzduRHx8fJlP5CUiIiIyplI9McOHD9d7//bbbyMuLg7Hjh1Ds2bNsH79eiQkJGDQoEEAgA0bNqB9+/Y4duwY/Pz8sG/fPly8eBHffPMN3N3d0a1bNyxduhRz585FVFQUbGxsTNcyIiIiqteqfE1McXExEhMTkZeXB7VajYyMDGi1Wvj7+0t12rVrB29vb6SlpcHPzw9paWno3Lmz3umlwMBAhISE4MKFC9Ij0h+l0Wig0Wik97m5uQAedFNptdoKxaurV9H6dYVc4wbkG7tc4wZME7sc201EDVOlk5hz585BrVajoKAAjo6O2Lp1Kzp06IAzZ87AxsYGLi4uevXd3d2RlZUFAMjKytJLYHTTddNKEx0djcWLFxuU79u3D/b29pWKPzk5uVL16wq5xg3IN3a5xg1UL/b8/HwTRkJEVHMqncS0bdsWZ86cQU5ODrZs2YLg4GCkpqbWRGyS+fPnIzw8XHqvu7o5ICCgUhf2JicnY8iQIXXmQqlOUXvLraO0EFjaswSLTlpAU1L2hVDnowJNFZpJ1MV1XhFyjRswTey6nk6ih7WYt9Ok87u2LMik86OGqdJJjI2NDVq3bg0A6NGjB06cOIHVq1djzJgxKCwsxN27d/V6Y7Kzs+Hh4QEA8PDwwPHjx/Xml52dLU0rjVKphFKpNCi3trau9IG6Kp+pKZriil+drSlRlFu/rrTrUXVpnVeGXOMGqhe7XNtMRA1PtYfLKykpgUajQY8ePWBtbY2UlBRpWmZmJq5fvw61Wg0AUKvVOHfuHG7fvi3VSU5OhkqlQocOHaobChERETUgleqJmT9/PoYNGwZvb2/cu3cPCQkJOHjwIPbu3QtnZ2dMnToV4eHhcHV1hUqlwsyZM6FWq+Hn5wcACAgIQIcOHTBx4kTExMQgKysLCxcuRGhoqNGeFiIiIqLSVCqJuX37NiZNmoRbt27B2dkZXbp0wd69ezFkyBAAwHvvvQcLCwuMHj1ab7A7HUtLSyQlJSEkJARqtRoODg4IDg7GkiVLTNsqIiIiqvcqlcSsX7++zOm2traIjY1FbGxsqXV8fHywa9euyiyWiIiIyEDDe0QtERER1QtMYoiIiEiWZPkUayIiKlt547ooLQViej8Yr6oywz0Q1SXsiSEiIiJZYk8MERHVOlOOAHxpaYDJ5kXywp4YIiIikiUmMURERCRLTGKIiIhIlpjEEBERkSwxiSEiIiJZYhJDREREssQkhoiIiGSJSQwRERHJEpMYIiIikiUmMURERCRLTGKIiIhIlpjEEBERkSwxiSEiIiJZYhJDREREssQkhoiIiGSJSQwR1QnR0dHo1asXnJyc4ObmhpEjRyIzM1OvTkFBAUJDQ9G4cWM4Ojpi9OjRyM7O1qtz/fp1BAUFwd7eHm5ubpgzZw6KiopqsylEVEuYxBBRnZCamorQ0FAcO3YMycnJ0Gq1CAgIQF5enlRn9uzZ2LFjBxITE5GamoqbN29i1KhR0vTi4mIEBQWhsLAQR48excaNGxEfH4+IiAhzNImIapiVuQMgIgKAPXv26L2Pj4+Hm5sbMjIy0L9/f+Tk5GD9+vVISEjAoEGDAAAbNmxA+/btcezYMfj5+WHfvn24ePEivvnmG7i7u6Nbt25YunQp5s6di6ioKNjY2BgsV6PRQKPRSO9zc3MBAFqtFlqtVirX/f/hsrpMaSnKnm4h9P6VM7l9N+WpT+15tC2mbhOTGCKqk3JycgAArq6uAICMjAxotVr4+/tLddq1awdvb2+kpaXBz88PaWlp6Ny5M9zd3aU6gYGBCAkJwYULF9C9e3eD5URHR2Px4sUG5fv27YO9vb1BeXJycrXbVhtieles3tKeJTUbSC3QfSdy+W4qqj61R9eW/Px8k86XSQwR1TklJSUICwtD37590alTJwBAVlYWbGxs4OLiolfX3d0dWVlZUp2HExjddN00Y+bPn4/w8HDpfW5uLpo3b46AgACoVCqpXKvVIjk5GUOGDIG1tXW121jTOkXtLXO60kJgac8SLDppAU2JopaiqhmnFwyS1XdTHrlta2V5tC26nk5TYRJDRHVOaGgozp8/j8OHD9f4spRKJZRKpUG5tbW10R+Q0srrGk1xxRITTYmiwnXrKt33IZfvpqLqU3t0bTF1e5jE1CMt5u002byuLQsy2byIKmPGjBlISkrCoUOH0KxZM6ncw8MDhYWFuHv3rl5vTHZ2Njw8PKQ6x48f15uf7u4lXR0iqj94dxIR1QlCCMyYMQNbt27F/v374evrqze9R48esLa2RkpKilSWmZmJ69evQ61WAwDUajXOnTuH27dvS3WSk5OhUqnQoUOH2mkIEdUa9sQQUZ0QGhqKhIQEbN++HU5OTtI1LM7OzrCzs4OzszOmTp2K8PBwuLq6QqVSYebMmVCr1fDz8wMABAQEoEOHDpg4cSJiYmKQlZWFhQsXIjQ01OgpIyKSNyYxRFQnxMXFAQAGDhyoV75hwwZMnjwZAPDee+/BwsICo0ePhkajQWBgID788EOprqWlJZKSkhASEgK1Wg0HBwcEBwdjyZIltdUMIqpFTGKIqE4QovzxSmxtbREbG4vY2NhS6/j4+GDXrl2mDI2I6igmMZVkyotniYiIqOp4YS8RERHJEpMYIiIikiUmMURERCRLTGKIiIhIlpjEEBERkSwxiSEiIiJZYhJDREREssQkhoiIiGSpUklMdHQ0evXqBScnJ7i5uWHkyJHIzMzUq1NQUIDQ0FA0btwYjo6OGD16tPQUWZ3r168jKCgI9vb2cHNzw5w5c1BUVFT91hAREVGDUakkJjU1FaGhoTh27BiSk5Oh1WoREBCAvLw8qc7s2bOxY8cOJCYmIjU1FTdv3sSoUaOk6cXFxQgKCkJhYSGOHj2KjRs3Ij4+HhEREaZrFREREdV7lXrswJ49e/Tex8fHw83NDRkZGejfvz9ycnKwfv16JCQkYNCgQQAePLytffv2OHbsGPz8/LBv3z5cvHgR33zzDdzd3dGtWzcsXboUc+fORVRUFGxsbEzXOiIiIqq3qvXspJycHACAq6srACAjIwNarRb+/v5SnXbt2sHb2xtpaWnw8/NDWloaOnfuDHd3d6lOYGAgQkJCcOHCBXTv3t1gORqNBhqNRnqfm5sLANBqtdBqtRWKVVevovVLo7Qs/yF1pqS0EHr/1pbqrqeH52GKedUmucYNmCZ2ObabiBqmKicxJSUlCAsLQ9++fdGpUycAQFZWFmxsbODi4qJX193dHVlZWVKdhxMY3XTdNGOio6OxePFig/J9+/bB3t6+UnEnJydXqv6jYnpX6+NVtrRnSa0uz5RPAa7uOjcXucYNVC/2/Px8E0ZCRFRzqpzEhIaG4vz58zh8+LAp4zFq/vz5CA8Pl97n5uaiefPmCAgIgEqlqtA8tFotkpOTMWTIEFhbW1c5lk5Re6v82apQWggs7VmCRSctoClR1Npyz0cFVnseplrntU2ucQOmiV3X00lEVNdVKYmZMWMGkpKScOjQITRr1kwq9/DwQGFhIe7evavXG5OdnQ0PDw+pzvHjx/Xmp7t7SVfnUUqlEkql0qDc2tq60gfqqnzmYZri2ksk9JZboqjVZZvyx7u669xc5Bo3UL3Y5dpmImp4KnV3khACM2bMwNatW7F//374+vrqTe/Rowesra2RkpIilWVmZuL69etQq9UAALVajXPnzuH27dtSneTkZKhUKnTo0KE6bSEiIqIGpFI9MaGhoUhISMD27dvh5OQkXcPi7OwMOzs7ODs7Y+rUqQgPD4erqytUKhVmzpwJtVoNPz8/AEBAQAA6dOiAiRMnIiYmBllZWVi4cCFCQ0ON9rYQERERGVOpJCYuLg4AMHDgQL3yDRs2YPLkyQCA9957DxYWFhg9ejQ0Gg0CAwPx4YcfSnUtLS2RlJSEkJAQqNVqODg4IDg4GEuWLKleS4iIiKhBqVQSI0T5t/na2toiNjYWsbGxpdbx8fEx6d0vRERE1PDw2UlEREQkS0xiiIiISJaYxBAREZEsMYkhIiIiWWISQ0RERLLEJIaIiIhkiUkMERERyRKTGCIiIpIlJjFEREQkS0xiiIiISJaYxBAREZEsMYkhIiIiWWISQ0RERLLEJIaIiIhkiUkMERERyRKTGCIiIpIlJjFEREQkS0xiiIiISJaYxBAREZEsMYkhIiIiWWISQ0RERLLEJIaIiIhkiUkMERERyRKTGCIiIpIlJjFEREQkS0xiiIiISJaYxBAREZEsMYkhIiIiWWISQ0RERLLEJIaIiIhkiUkMEdUZhw4dwvDhw+Hl5QWFQoFt27bpTRdCICIiAp6enrCzs4O/vz8uXbqkV+fOnTuYMGECVCoVXFxcMHXqVNy/f78WW0FEtYVJDBHVGXl5eejatStiY2ONTo+JicGaNWuwdu1apKenw8HBAYGBgSgoKJDqTJgwARcuXEBycjKSkpJw6NAhTJ8+vbaaQES1yMrcARAR6QwbNgzDhg0zOk0IgVWrVmHhwoUYMWIEAOCzzz6Du7s7tm3bhrFjx+L777/Hnj17cOLECfTs2RMA8P777+Ppp5/GypUr4eXlVWttIaKaxySGiGTh6tWryMrKgr+/v1Tm7OyMPn36IC0tDWPHjkVaWhpcXFykBAYA/P39YWFhgfT0dDz33HMG89VoNNBoNNL73NxcAIBWq4VWq5XKdf9/uKwuU1qKsqdbCL1/5Uxu30156lN7Hm2LqdvEJIaIZCErKwsA4O7urlfu7u4uTcvKyoKbm5vedCsrK7i6ukp1HhUdHY3FixcblO/btw/29vYG5cnJyVWKv7bF9K5YvaU9S2o2kFqg+07k8t1UVH1qj64t+fn5Jp0vkxgiatDmz5+P8PBw6X1ubi6aN2+OgIAAqFQqqVyr1SI5ORlDhgyBtbW1OUKtlE5Re8ucrrQQWNqzBItOWkBToqilqGrG6QWDZPXdlEdu21pZHm2LrqfTVJjEEJEseHh4AACys7Ph6ekplWdnZ6Nbt25Sndu3b+t9rqioCHfu3JE+/yilUgmlUmlQbm1tbfQHpLTyukZTXLHERFOiqHDdukr3fcjlu6mo+tQeXVtM3R4mMWRUi3k7qz0PpaVATO8HfxFmvv2MCaKihszX1xceHh5ISUmRkpbc3Fykp6cjJCQEAKBWq3H37l1kZGSgR48eAID9+/ejpKQEffr0MVfoFWaK/a4h6hS1VzrWmCIhu7YsyARRUW1gEkNEdcb9+/dx+fJl6f3Vq1dx5swZuLq6wtvbG2FhYXjrrbfQpk0b+Pr6YtGiRfDy8sLIkSMBAO3bt8fQoUMxbdo0rF27FlqtFjNmzMDYsWN5ZxJRPcQkhojqjJMnT+Kpp56S3uuuVQkODkZ8fDzefPNN5OXlYfr06bh79y6efPJJ7NmzB7a2ttJnNm3ahBkzZmDw4MGwsLDA6NGjsWbNmlpvCxHVPCYxRFRnDBw4EEKUfsuvQqHAkiVLsGTJklLruLq6IiEhoSbCI6I6ptIj9nJYcCIiIqoLKp3EcFhwIiIiqgsqfTqJw4ITERFRXWDSa2LMPSx4WUw15HF5Q3mbmpyHBn84djkNny3nIb9NEbsc201kSqa81Z23a9cskyYxdWVY8LJUdxjnig7lbWpyHhp8ac8S7Nq1y9xhVJqch/yuTuymHhaciKimyOLupIoOC14WUw3jXN5Q3qYm56HBH449I2KoucOpMDkP+W2K2E09LDgRUU0xaRJTV4YFL0t1hz021/Dcch4aXFOikF0yAMh7yO/qxC7XNhNRw2PSJKYhDAtOVWPq4dR5npmIiCqdxHBYcCIiIqoLKp3EcFhwIiIiqgsqncRwWHAiIiKqCyo9Yi8RERFRXcAkhoiIiGSJSQwRERHJEpMYIiIikiUmMURERCRLTGKIiIhIlpjEEBERkSwxiSEiIiJZYhJDREREssQkhoiIiGSJSQwRERHJEpMYIiIikiUmMURERCRLTGKIiIhIlpjEEBERkSwxiSEiIiJZYhJDREREssQkhoiIiGTJytwBEBER1Vct5u2s9GeUlgIxvYFOUXuhKVboTbu2LMhUodUL7IkhIiIiWWISQ0RERLLEJIaIiIhkiUkMERERyRKTGCIiIpIlJjFEREQkS7zFmmSpKrctloa3LBIRyRN7YoiIiEiWmMQQERGRLDGJISIiIlliEkNERESyVO8v7NVdAFrWsyiIiIhIftgTQ0RERLLEJIaIiIhkqd6fTiIiqimmHK+IiCqPPTFEREQkS+yJoQbv0b+mq3sROEcAJqKaYureP7kfr9gTQ0RERLLEJIaIiIhkiUkMERERyRKviSEyMT5hm4iodpi1JyY2NhYtWrSAra0t+vTpg+PHj5szHCKqR3h8Iar/zJbE/Pe//0V4eDgiIyNx6tQpdO3aFYGBgbh9+7a5QiKieoLHF6KGwWynk959911MmzYNU6ZMAQCsXbsWO3fuxKeffop58+aZKyyiOqWyp6bKuz28oZye4vGFqGEwSxJTWFiIjIwMzJ8/XyqzsLCAv78/0tLSDOprNBpoNBrpfU5ODgDgzp070Gq1ZS7Lqijvwb8lAvn5JbDSWqC4RD4PgJRr3IB8Y5dr3ED5sf/xxx/lzuPevXsAACGEyeOrDTV1fNFqtcjPz8cff/wBa2trAH8fX+RIztv5o+pTW4DabU9FjgnV8eh+Y/LjizCDX3/9VQAQR48e1SufM2eO6N27t0H9yMhIAYAvvviqxdeNGzdq65BgUjy+8MVX3X+Z6vgii7uT5s+fj/DwcOl9SUkJ7ty5g8aNG0OhqFiWmpubi+bNm+PGjRtQqVQ1FarJyTVuQL6xyzVuwDSxCyFw7949eHl5mTi6uqmixxc5bxfG1Kf21Ke2APWrPY+2xdTHF7MkMU2aNIGlpSWys7P1yrOzs+Hh4WFQX6lUQqlU6pW5uLhUadkqlUqWG4Vc4wbkG7tc4waqH7uzs7MJo6ldNX18kfN2YUx9ak99agtQv9rzcFtMeXwxy91JNjY26NGjB1JSUqSykpISpKSkQK1WmyMkIqoneHwhajjMdjopPDwcwcHB6NmzJ3r37o1Vq1YhLy9PupuAiKiqeHwhahjMlsSMGTMGv/32GyIiIpCVlYVu3bphz549cHd3r5HlKZVKREZGGnQb13VyjRuQb+xyjRuQd+ymVBPHl/q2butTe+pTW4D61Z6abotCCJneR0lEREQNGh8ASURERLLEJIaIiIhkiUkMERERyRKTGCIiIpIlJjFEREQkS/U6iYmKioJCodB7tWvXztxhGXXo0CEMHz4cXl5eUCgU2LZtm950IQQiIiLg6ekJOzs7+Pv749KlS+YJ9iHlxT158mSD72Do0KHmCfYh0dHR6NWrF5ycnODm5oaRI0ciMzNTr05BQQFCQ0PRuHFjODo6YvTo0QajwJpDRWIfOHCgwXp/7bXXzBRx3WWK/e7OnTuYMGECVCoVXFxcMHXqVNy/f78WW/E3U23X169fR1BQEOzt7eHm5oY5c+agqKioNpuCuLg4dOnSRRrpVa1WY/fu3bJrhzHLli2DQqFAWFiYVCan9pT321qbbanXSQwAdOzYEbdu3ZJehw8fNndIRuXl5aFr166IjY01Oj0mJgZr1qzB2rVrkZ6eDgcHBwQGBqKgoKCWI9VXXtwAMHToUL3v4Msvv6zFCI1LTU1FaGgojh07huTkZGi1WgQEBCAv7++nEs+ePRs7duxAYmIiUlNTcfPmTYwaNcqMUT9QkdgBYNq0aXrrPSYmxkwR112m2O8mTJiACxcuIDk5GUlJSTh06BCmT59eW03QY4rturi4GEFBQSgsLMTRo0exceNGxMfHIyIiolbb0qxZMyxbtgwZGRk4efIkBg0ahBEjRuDChQuyasejTpw4gY8++ghdunTRK5dbe8r6ba3VtpjkMZJ1VGRkpOjatau5w6g0AGLr1q3S+5KSEuHh4SFWrFghld29e1colUrx5ZdfmiFC4x6NWwghgoODxYgRI8wST2Xcvn1bABCpqalCiAfr19raWiQmJkp1vv/+ewFApKWlmStMox6NXQghBgwYIGbNmmW+oGSoKvvdxYsXBQBx4sQJqc7u3buFQqEQv/76a63FXpqqbNe7du0SFhYWIisrS6oTFxcnVCqV0Gg0tduARzRq1Eh88sknsm3HvXv3RJs2bURycrLePiq39pT121rbban3PTGXLl2Cl5cXWrZsiQkTJuD69evmDqnSrl69iqysLPj7+0tlzs7O6NOnD9LS0swYWcUcPHgQbm5uaNu2LUJCQvDHH3+YOyQDOTk5AABXV1cAQEZGBrRard46b9euHby9vevcOn80dp1NmzahSZMm6NSpE+bPn4/8/HxzhCdbFdnv0tLS4OLigp49e0p1/P39YWFhgfT09FqP+VFV2a7T0tLQuXNnvdGNAwMDkZubK/WC1Lbi4mJs3rwZeXl5UKvVsm1HaGgogoKC9OIG5Pm9lPbbWtttMdtjB2pDnz59EB8fj7Zt2+LWrVtYvHgx+vXrh/Pnz8PJycnc4VVYVlYWABgMme7u7i5Nq6uGDh2KUaNGwdfXF1euXMG///1vDBs2DGlpabC0tDR3eAAePBwwLCwMffv2RadOnQA8WOc2NjYGTzOua+vcWOwAMH78ePj4+MDLywtnz57F3LlzkZmZia+//tqM0cpLRfa7rKwsuLm56U23srKCq6ur2beTqm7XWVlZRtusm1abzp07B7VajYKCAjg6OmLr1q3o0KEDzpw5I6t2AMDmzZtx6tQpnDhxwmCa3L6Xsn5ba7st9TqJGTZsmPT/Ll26oE+fPvDx8cFXX32FqVOnmjGyhmPs2LHS/zt37owuXbqgVatWOHjwIAYPHmzGyP4WGhqK8+fP19nrpcpSWuwPX5PRuXNneHp6YvDgwbhy5QpatWpV22GSGch5u9Zp27Ytzpw5g5ycHGzZsgXBwcFITU01d1iVduPGDcyaNQvJycmwtbU1dzjVVtZvq52dXa3GUu9PJz3MxcUFjz32GC5fvmzuUCrFw8MDAAyu7s7OzpamyUXLli3RpEmTOvMdzJgxA0lJSThw4ACaNWsmlXt4eKCwsBB3797Vq1+X1nlpsRvTp08fAKgz610OKrLfeXh44Pbt23rTi4qKcOfOHbNuJ9XZrj08PIy2WTetNtnY2KB169bo0aMHoqOj0bVrV6xevVp27cjIyMDt27fx+OOPw8rKClZWVkhNTcWaNWtgZWUFd3d3WbXnUQ//ttb2d9Ogkpj79+/jypUr8PT0NHcoleLr6wsPDw+kpKRIZbm5uUhPT4darTZjZJX3yy+/4I8//jD7dyCEwIwZM7B161bs378fvr6+etN79OgBa2trvXWemZmJ69evm32dlxe7MWfOnAEAs693OanIfqdWq3H37l1kZGRIdfbv34+SkhIpcaxNptiu1Wo1zp07p5ecJScnQ6VSoUOHDrXTkFKUlJRAo9HIrh2DBw/GuXPncObMGenVs2dPTJgwQfq/nNrzqId/W2v9u6nkRcmy8vrrr4uDBw+Kq1eviiNHjgh/f3/RpEkTcfv2bXOHZuDevXvi9OnT4vTp0wKAePfdd8Xp06fFzz//LIQQYtmyZcLFxUVs375dnD17VowYMUL4+vqKv/76q87Gfe/ePfHGG2+ItLQ0cfXqVfHNN9+Ixx9/XLRp00YUFBSYNe6QkBDh7OwsDh48KG7duiW98vPzpTqvvfaa8Pb2Fvv37xcnT54UarVaqNVqM0b9QHmxX758WSxZskScPHlSXL16VWzfvl20bNlS9O/f38yR1z2m2O+GDh0qunfvLtLT08Xhw4dFmzZtxLhx48zSHlNs10VFRaJTp04iICBAnDlzRuzZs0c0bdpUzJ8/v1bbMm/ePJGamiquXr0qzp49K+bNmycUCoXYt2+frNpRmkfvIJRTe8r7ba3NttTrJGbMmDHC09NT2NjYiH/84x9izJgx4vLly+YOy6gDBw4IAAav4OBgIcSD2z0XLVok3N3dhVKpFIMHDxaZmZnmDVqUHXd+fr4ICAgQTZs2FdbW1sLHx0dMmzZN77Y6czEWMwCxYcMGqc5ff/0l/vnPf4pGjRoJe3t78dxzz4lbt26ZL+j/r7zYr1+/Lvr37y9cXV2FUqkUrVu3FnPmzBE5OTnmDbwOMsV+98cff4hx48YJR0dHoVKpxJQpU8S9e/fM0BrTbdfXrl0Tw4YNE3Z2dqJJkybi9ddfF1qttlbb8vLLLwsfHx9hY2MjmjZtKgYPHiwlMHJqR2keTWLk1J7yfltrsy0KIYSoXN8NERERkfk1qGtiiIiIqP5gEkNERESyxCSGiIiIZIlJDBEREckSkxgiIiKSJSYxREREJEtMYoiIiEiWmMQQERGRLDGJISIiIlliEkNERESyxCSGiIiIZOn/AY2Za3u+2UlOAAAAAElFTkSuQmCC"/>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=6a571750-43a1-49f1-9d8f-44f6980399d7">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [119]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">FUELCONSUMPTION_COMB</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">CO2EMISSIONS</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s2">"CO2EMISSIONS"</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s2">"FUELCONSUMPTION_COMB"</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[119]:</div>
<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain" tabindex="0">
<pre>[]</pre>
</div>
</div>
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedImage jp-OutputArea-output" tabindex="0">
<img alt="No description has been provided for this image" class="" src="data:image/png;base64,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"/>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=a8084633-7a27-491a-afcd-afce54138882">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [120]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">ENGINESIZE</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">CO2EMISSIONS</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s2">"CO2EMISSIONS"</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s2">"ENGINESIZE"</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[120]:</div>
<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain" tabindex="0">
<pre>[]</pre>
</div>
</div>
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedImage jp-OutputArea-output" tabindex="0">
<img alt="No description has been provided for this image" class="" src="data:image/png;base64,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"/>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=252c1dba-be0b-424f-beb2-18e62a603890">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h3 id="Data-separation">Data separation<a class="anchor-link" href="#Data-separation">¶</a></h3>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=6dc40bc3-fc3e-4f59-839a-a8ac26cf680f">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [121]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">df</span><span class="p">[[</span><span class="s2">"ENGINESIZE"</span><span class="p">,</span> <span class="s2">"CYLINDERS"</span><span class="p">,</span> <span class="s2">"FUELCONSUMPTION_COMB"</span><span class="p">]]</span><span class="o">.</span><span class="n">values</span>
<span class="n">y</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s2">"CO2EMISSIONS"</span><span class="p">]</span><span class="o">.</span><span class="n">values</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">y</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
<pre>(1067, 3)
(1067,)
</pre>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=e89516e6-6ea8-4b7e-8d34-57e15a559c65">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [122]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="kn">import</span> <span class="n">train_test_split</span>
<span class="n">x_train</span><span class="p">,</span> <span class="n">x_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">x</span><span class="p">,</span><span class="n">y</span><span class="p">,</span> <span class="n">test_size</span><span class="o">=</span><span class="mf">0.2</span><span class="p">,</span> <span class="n">random_state</span><span class="o">=</span><span class="mi">4</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x_test</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">y_test</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x_train</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">y_train</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
<pre>(214, 3) (214,)
(853, 3) (853,)
</pre>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=6214df56-d9fe-4f06-ab9f-8a33be9700ff">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h3 id="multiple-linear-regression">multiple linear regression<a class="anchor-link" href="#multiple-linear-regression">¶</a></h3>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=dfb3ae6e-e78e-4bcf-88e7-f5a2529d8c7a">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [123]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn</span> <span class="kn">import</span> <span class="n">linear_model</span>
<span class="n">regr</span> <span class="o">=</span> <span class="n">linear_model</span><span class="o">.</span><span class="n">LinearRegression</span><span class="p">()</span>
<span class="n">regr</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">regr</span><span class="o">.</span><span class="n">coef_</span><span class="p">,</span> <span class="n">regr</span><span class="o">.</span><span class="n">intercept_</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
<pre>[10.24537129  7.64355532  9.68132732] 65.25787570246109
</pre>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=f398cb91-868c-471d-b155-58c6c83253e9">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h2 id="Evalution">Evalution<a class="anchor-link" href="#Evalution">¶</a></h2>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=90c1b1f3-9c54-48c1-ad11-8162deead8bc">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [124]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="kn">import</span> <span class="n">r2_score</span>
<span class="n">yhat</span> <span class="o">=</span> <span class="n">regr</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">x_test</span><span class="p">)</span>
<span class="n">r2_score</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span> <span class="n">yhat</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[124]:</div>
<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain" tabindex="0">
<pre>0.890023090970219</pre>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=5494d7f5-b9b9-4dc5-ac93-89e1a522824c">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [125]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">mpl_toolkits.mplot3d</span> <span class="kn">import</span> <span class="n">Axes3D</span>


<span class="c1"># Create the plot</span>
<span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">fig</span><span class="o">.</span><span class="n">add_subplot</span><span class="p">(</span><span class="mi">111</span><span class="p">,</span> <span class="n">projection</span><span class="o">=</span><span class="s1">'3d'</span><span class="p">)</span>

<span class="c1"># Define the independent variables</span>
<span class="n">x</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">'ENGINESIZE'</span><span class="p">]</span>
<span class="n">y</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">'CYLINDERS'</span><span class="p">]</span>
<span class="n">z</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">'FUELCONSUMPTION_COMB'</span><span class="p">]</span>
<span class="n">cm</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">get_cmap</span><span class="p">(</span><span class="s2">"RdYlGn"</span><span class="p">)</span>
<span class="n">col</span> <span class="o">=</span> <span class="p">[</span><span class="n">cm</span><span class="p">(</span><span class="nb">float</span><span class="p">(</span><span class="n">i</span><span class="p">)</span><span class="o">/</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">x</span><span class="p">)))</span> <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">x</span><span class="p">))]</span>

<span class="c1"># Add the data points</span>
<span class="n">ax</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">,</span> <span class="n">z</span><span class="p">,</span> <span class="n">c</span><span class="o">=</span><span class="n">col</span><span class="p">,</span> <span class="n">marker</span><span class="o">=</span><span class="s1">'o'</span><span class="p">)</span>

<span class="c1"># Fit a plane using np.linalg.lstsq</span>
<span class="n">A</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">vstack</span><span class="p">([</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">ones_like</span><span class="p">(</span><span class="n">x</span><span class="p">)])</span><span class="o">.</span><span class="n">T</span>
<span class="n">plane_coef</span><span class="p">,</span> <span class="n">_</span><span class="p">,</span> <span class="n">_</span><span class="p">,</span> <span class="n">_</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">linalg</span><span class="o">.</span><span class="n">lstsq</span><span class="p">(</span><span class="n">A</span><span class="p">,</span> <span class="n">z</span><span class="p">,</span> <span class="n">rcond</span><span class="o">=</span><span class="kc">None</span><span class="p">)</span>

<span class="c1"># Create a meshgrid for the plane</span>
<span class="n">x_plane</span><span class="p">,</span> <span class="n">y_plane</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">meshgrid</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">)</span>
<span class="n">z_plane</span> <span class="o">=</span> <span class="n">plane_coef</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">*</span> <span class="n">x_plane</span> <span class="o">+</span> <span class="n">plane_coef</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span> <span class="o">*</span> <span class="n">y_plane</span> <span class="o">+</span> <span class="n">plane_coef</span><span class="p">[</span><span class="mi">2</span><span class="p">]</span>

<span class="c1"># Add the regression plane</span>
<span class="n">ax</span><span class="o">.</span><span class="n">plot_surface</span><span class="p">(</span><span class="n">x_plane</span><span class="p">,</span> <span class="n">y_plane</span><span class="p">,</span> <span class="n">z_plane</span><span class="p">,</span> <span class="n">alpha</span><span class="o">=</span><span class="mf">0.5</span><span class="p">)</span>

<span class="c1"># Add labels and title</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_xlabel</span><span class="p">(</span><span class="s1">'ENGINESIZE'</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_ylabel</span><span class="p">(</span><span class="s1">'CYLINDERS'</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">set_zlabel</span><span class="p">(</span><span class="s1">'FUELCONSUMPTION_COMB'</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">'Multiple Linear Regression co2 emissions'</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[125]:</div>
<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain" tabindex="0">
<pre>Text(0.5, 0.92, 'Multiple Linear Regression co2 emissions')</pre>
</div>
</div>
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedImage jp-OutputArea-output" tabindex="0">
<img alt="No description has been provided for this image" class="" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAZcAAAGhCAYAAACtRfm9AAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjkuMiwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8hTgPZAAAACXBIWXMAAA9hAAAPYQGoP6dpAAD1g0lEQVR4nOz9d3wcV73/jz9nZqt6sSxbLrIs9xLbcRzHdhpJiGNCTSAELpCQQIBPqOEL93dpKXRyueTSkktLg1wuJYF7AyQhIRBSCbYky02usizZVq/bZ+b8/ljNeHe1K22ZVXHm+XjwIF7tzjk7O3Ne836fd5GEEAIbGxsbGxsLkad6AjY2NjY2Zx+2uNjY2NjYWI4tLjY2NjY2lmOLi42NjY2N5djiYmNjY2NjOba42NjY2NhYji0uNjY2NjaWY4uLjY2NjY3l2OJiY2NjY2M5Z4243HHHHUiSlNZ7H3jgASRJorW1NeNx/vrXvyJJEn/9618z/mwuLFq0iBtvvHFSx7SxllyuO5vMyde92traiiRJPPDAA5Ye92xjUsTFuKkkSeL5558f83chBAsWLECSJN74xjdaNu7XvvY1fve731l2vHxgXKj//u//PtVTyRvGTW78T1EUZs+ezdvf/nb2798/1dOzyZBHH32Ud77znSxevJiCggKWL1/Opz/9aQYGBqZ6ajbTCMdkDubxeHjkkUe48MIL417/29/+Rnt7O26329Lxvva1r/H2t7+dt771rXGvv/e97+X666+3fLx80tLSgizPbEPz4x//OJs2bSISibB7927uu+8+/vrXv7Jnzx7mzJkz1dPLOzPxukvGLbfcQk1NDe95z3tYuHAhzc3NfP/73+ePf/wju3btwuv1TvUUAbj44osJBAK4XC5Lj1tbW0sgEMDpdFp63LONSRWXN7zhDfz617/mu9/9Lg7HmaEfeeQRNm7cSE9Pz6TMQ1EUFEWZlLGsYrovSD6fj8LCwnHfc9FFF/H2t7/d/Pfy5cv5yEc+wkMPPcRnP/vZfE8xDr/fT0FBwaSOOROvu2T85je/4dJLL417bePGjdxwww384he/4AMf+MDUTCwBWZbxeDyWH1eSpLwc92xjUh+F3/Wud9Hb28uf//xn87VwOMxvfvMb3v3ud495fyqfaTo+T0mS8Pl8PPjgg6Y7xtizSOb7XrRoEW984xt56qmnWL9+PR6Ph1WrVvHoo4+m9d1eeeUVrrrqKkpLSykoKOCSSy7hhRdeSOuz6ZC452J8hxdeeIHbbruNqqoqCgsLedvb3kZ3d/eYz//pT3/ioosuorCwkOLiYq6++mr27t0b957du3dz4403snjxYjweD3PmzOGmm26it7c37n3G/ta+fft497vfTXl5+RhrNB0uuugiAI4cORL3ekdHBzfddBPV1dW43W5Wr17Nz372szGfP378OG9+85spLCxk9uzZfOpTn+LJJ58cc81ceumlrFmzhp07d3LxxRdTUFDA5z73OQBCoRC33347S5Yswe12s2DBAj772c8SCoXixvrzn//MhRdeSFlZGUVFRSxfvtw8hsH3vvc9Vq9eTUFBAeXl5Zx33nk88sgj5t9T7bn88Ic/ZPXq1bjdbmpqarj11lvHuJiM77Bv3z5e97rXUVBQwLx58/jWt76V1rkG+PnPf875559vzu/iiy/mqaeeymouibztbW8DSNvNmc71eOONN1JUVERbWxtvfOMbKSoqYt68efzgBz8AoLm5mcsuu4zCwkJqa2vjzjUkXz8OHTrEtddey5w5c/B4PMyfP5/rr7+ewcFB8z0T/dap1p+//OUv5ncqKyvjLW95y5jzYdw7hw8f5sYbb6SsrIzS0lLe//734/f7496bzjU3nZlUy2XRokVs2bKF//7v/2bHjh1A9CIbHBzk+uuv57vf/a5lYz388MN84AMf4Pzzz+eWW24BoL6+ftzPHDp0iHe+8518+MMf5oYbbuD+++/nHe94B0888QSvf/3rU37uL3/5Czt27GDjxo3cfvvtyLLM/fffz2WXXcbf//53zj//fMu+VyIf+9jHKC8v5/bbb6e1tZV77rmHj370o/zP//yP+Z6HH36YG264ge3bt/PNb34Tv9/Pvffey4UXXkhDQwOLFi0Cohfz0aNHef/738+cOXPYu3cvP/rRj9i7dy8vv/zymICJd7zjHSxdupSvfe1rZNO5wVhky8vLzdc6Ozu54IILkCSJj370o1RVVfGnP/2Jm2++maGhIT75yU8CUUvpsssu49SpU3ziE59gzpw5PPLIIzz77LNJx+rt7WXHjh1cf/31vOc976G6uhpd13nzm9/M888/zy233MLKlStpbm7mO9/5DgcPHjT36/bu3csb3/hGzjnnHO666y7cbjeHDx+Oe3j48Y9/zMc//nHe/va384lPfIJgMMju3bt55ZVXkj44Gdxxxx3ceeedXHHFFXzkIx+hpaWFe++9l1dffZUXXnghzvXS39/PVVddxTXXXMN1113Hb37zG/71X/+VtWvXmvdTKu68807uuOMOtm7dyl133YXL5eKVV17hL3/5C1deeWXGc0nk9OnTAMyaNWvceUD61yOApmns2LGDiy++mG9961v84he/4KMf/SiFhYV8/vOf51/+5V+45ppruO+++3jf+97Hli1bqKurSzpuOBxm+/bthEIhPvaxjzFnzhw6Ojp4/PHHGRgYoLS0NK3fOhlPP/00O3bsYPHixdxxxx0EAgG+973vsW3bNnbt2hX3nQCuu+466urq+PrXv86uXbv4yU9+wuzZs/nmN78JpHfNTXvEJHD//fcLQLz66qvi+9//viguLhZ+v18IIcQ73vEO8brXvU4IIURtba24+uqrzc89++yzAhDPPvts3PGOHTsmAHH//febr91+++0i8esUFhaKG264IeV8jh07Zr5WW1srAPHb3/7WfG1wcFDMnTtXbNiwIeWcdF0XS5cuFdu3bxe6rpvv8/v9oq6uTrz+9a8f99wY3+Xuu+8e9321tbVx38X4DldccUXcuJ/61KeEoihiYGBACCHE8PCwKCsrEx/84Afjjnf69GlRWloa97rxm8Ty3//93wIQzz33nPmaca7f9a53jTtnA+Oc/exnPxPd3d3i5MmT4oknnhBLliwRkiSJf/zjH+Z7b775ZjF37lzR09MTd4zrr79elJaWmnP89re/LQDxu9/9znxPIBAQK1asGHPNXHLJJQIQ9913X9wxH374YSHLsvj73/8e9/p9990nAPHCCy8IIYT4zne+IwDR3d2d8ju+5S1vEatXrx73PCRed11dXcLlcokrr7xSaJpmvu/73/++eb4Sv8NDDz1kvhYKhcScOXPEtddeO+64hw4dErIsi7e97W1x4wghzGsnk7kk4+abbxaKooiDBw+O+75MrscbbrhBAOJrX/ua+Vp/f7/wer1CkiTxy1/+0nz9wIEDAhC33367+VrivdrQ0CAA8etf/zrl/NL5rZOtP+vXrxezZ88Wvb295mtNTU1ClmXxvve9z3zNuHduuummuGO+7W1vE5WVlRnNY7oz6TvE1113HYFAgMcff5zh4WEef/zxcZ/sJpOamhrTvAcoKSnhfe97Hw0NDeaTWSKNjY0cOnSId7/73fT29tLT00NPTw8+n4/LL7+c5557Dl3X8zbnW265Jc6iuOiii9A0jePHjwNRa2RgYIB3vetd5tx6enpQFIXNmzfHPenHbsQGg0F6enq44IILANi1a9eYsT/84Q9nNNebbrqJqqoqampquOqqqxgcHOThhx9m06ZNQDRq8Le//S1vetObEELEzXf79u0MDg6a83jiiSeYN28eb37zm83jezwePvjBDyYd2+128/73vz/utV//+tesXLmSFStWxI112WWXAZjnpqysDIDf//73KX/LsrIy2tvbefXVV9M+H08//TThcJhPfvKTccEaH/zgBykpKeEPf/hD3PuLiop4z3veY/7b5XJx/vnnc/To0XHH+d3vfoeu63zpS18aExRiXDuZziWWRx55hJ/+9Kd8+tOfZunSpePOJZPr0SB2D6esrIzly5dTWFjIddddZ76+fPlyysrKxj0XpaWlADz55JNjXFCxx4fxf+tETp06RWNjIzfeeCMVFRXm6+eccw6vf/3r+eMf/zjmM4n3zkUXXURvby9DQ0NZz2O6MeniUlVVxRVXXMEjjzzCo48+iqZpcZu8U8mSJUvGuH6WLVsGkDI34dChQwDccMMNVFVVxf3vJz/5CaFQKM6fazULFy6M+7fhYurv74+b32WXXTZmfk899RRdXV3mZ/v6+vjEJz5BdXU1Xq+Xqqoq08WQ7Dukcj+k4ktf+hJ//vOfeeyxx3jf+97H4OBg3ELW3d3NwMAAP/rRj8bM1RAGY77Hjx+nvr5+zO+1ZMmSpGPPmzdvTNTQoUOH2Lt375ixjN/cGOud73wn27Zt4wMf+ADV1dVcf/31/OpXv4q76f/1X/+VoqIizj//fJYuXcqtt946oQvDeABYvnx53Osul4vFixebfzeYP3/+mO9bXl5u/tapOHLkCLIss2rVKsvmYvD3v/+dm2++me3bt/PVr3513HlAZtcjRB8Yqqqq4l4rLS1Nei5KS0vHPRd1dXXcdttt/OQnP2HWrFls376dH/zgB3HXdjq/dSKpzh3AypUrzYfNWCa6b7OZx3RjUvdcDN797nfzwQ9+kNOnT7Njxw5TpRNJlRSpaVoeZ5cZxo999913s379+qTvKSoqytv4qaKPxOgeiDG/hx9+OGm4b2zU3nXXXceLL77IZz7zGdavX09RURG6rnPVVVclvagzDTldu3YtV1xxBQBvfetb8fv9fPCDH+TCCy9kwYIF5hjvec97uOGGG5Ie45xzzslozPHmqus6a9eu5T/+4z+SfmbBggXmZ5977jmeffZZ/vCHP/DEE0/wP//zP1x22WU89dRTKIrCypUraWlp4fHHH+eJJ57gt7/9LT/84Q/50pe+xJ133pnVnBOZ6LeebJqamnjzm9/MmjVr+M1vfhN3LaUik+sRUn/nbM/Ft7/9bW688UZ+//vf89RTT/Hxj3+cr3/967z88svMnz8/rd/aCiaa/2TNI59Mibi87W1v40Mf+hAvv/xy3MZzIoaaJ0arpHqKSiTdjH2Dw4cPI4SI+9zBgwcBxmzIGRhBAiUlJebCOZ0w5jd79uxx59ff388zzzzDnXfeyZe+9CXzdeNJMx984xvf4LHHHuOrX/0q9913H1VVVRQXF6Np2oTnsra2ln379o35vQ4fPpz2+PX19TQ1NXH55ZdPeK3Isszll1/O5Zdfzn/8x3/wta99jc9//vM8++yz5lwLCwt55zvfyTvf+U7C4TDXXHMNX/3qV/m3f/u3pKGrtbW1QDSHafHixebr4XCYY8eOWXY91dfXo+s6+/btS/kAlOlcjhw5wlVXXcXs2bP54x//mPYDVLrXYz5Zu3Yta9eu5Qtf+AIvvvgi27Zt47777uMrX/kKkN5vHUvsuUvkwIEDzJo1a8Iw/WRkOo/pxpRk5RUVFXHvvfdyxx138KY3vSnl+2pra1EUheeeey7u9R/+8IdpjVNYWJhR1vDJkyd57LHHzH8PDQ3x0EMPsX79+pRJfhs3bqS+vp5///d/Z2RkZMzfk4UFTybbt2+npKSEr33ta0QikTF/N+ZnPAklPvndc889eZtbfX091157LQ888ACnT59GURSuvfZafvvb37Jnz56Uc4Xo9+ro6OB///d/zdeCwSA//vGP0x7/uuuuo6OjI+lnAoGA6cro6+sb83djkTZClhPDtV0uF6tWrUIIkfS8A1xxxRW4XC6++93vxp33n/70pwwODnL11Ven/V3G461vfSuyLHPXXXeNsUCNcTOZy+nTp7nyyiuRZZknn3xyjNtqPNK9HvPB0NAQqqrGvbZ27VpkWTZ/x3R+60Tmzp3L+vXrefDBB+PWmz179vDUU0/xhje8IeO5ZjOP6caUWC5ASrdHLKWlpbzjHe/ge9/7HpIkUV9fz+OPPz7GL5uKjRs38vTTT/Mf//Ef1NTUUFdXx+bNm1O+f9myZdx88828+uqrVFdX87Of/YzOzk7uv//+lJ+RZZmf/OQn7Nixg9WrV/P+97+fefPm0dHRwbPPPktJSQn/93//N+Fcn3nmGYLB4JjX3/rWt7JmzZq0vm8ySkpKuPfee3nve9/Lueeey/XXX09VVRVtbW384Q9/YNu2bXz/+9+npKTEDPeMRCLMmzePp556imPHjmU9djp85jOf4Ve/+hX33HMP3/jGN/jGN77Bs88+y+bNm/ngBz/IqlWr6OvrY9euXTz99NPmTfehD32I73//+7zrXe/iE5/4BHPnzuUXv/iFaSGkY7W+973v5Ve/+hUf/vCHefbZZ9m2bRuapnHgwAF+9atf8eSTT3Leeedx11138dxzz3H11VdTW1tLV1cXP/zhD5k/f76Z33PllVcyZ84ctm3bRnV1Nfv37+f73/8+V199NcXFxUnHr6qq4t/+7d+48847ueqqq3jzm99MS0sLP/zhD9m0aVPc5n0uLFmyhM9//vN8+ctf5qKLLuKaa67B7Xbz6quvUlNTw9e//vWM5nLVVVdx9OhRPvvZz/L888/HlXSqrq4eN2w/3esxH/zlL3/hox/9KO94xztYtmwZqqry8MMPmw81QFq/dTLuvvtuduzYwZYtW7j55pvNUOTS0lLuuOOOjOea7TymFZMRkhYbijweiaHIQgjR3d0trr32WlFQUCDKy8vFhz70IbFnz560QpEPHDggLr74YuH1egVghvKmCkW++uqrxZNPPinOOecc4Xa7xYoVK8aELaYKj25oaBDXXHONqKysFG63W9TW1orrrrtOPPPMM+N+ZyOsMdX/Hn74YXN+yUKRE89pqvk9++yzYvv27aK0tFR4PB5RX18vbrzxRvHPf/7TfE97e7t429veJsrKykRpaal4xzveIU6ePDkmxNM41+mGSRpzShUCeumll4qSkhIzfLqzs1PceuutYsGCBcLpdIo5c+aIyy+/XPzoRz+K+9zRo0fF1VdfLbxer6iqqhKf/vSnxW9/+1sBiJdfftl83yWXXJIyTDgcDotvfvObYvXq1cLtdovy8nKxceNGceedd4rBwUEhhBDPPPOMeMtb3iJqamqEy+USNTU14l3veldc2O1//dd/iYsvvtj8/evr68Vn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J0+epKWlBa/XawpNWVnZpNSxMkoo2ZbL+Ph8vryEIn/0ox/l8ccf57nnnovrxZSMzZs3A3D48GFbXCB/7YeNukJ9fX0sX77c0r72sVglLpFIhObmZoaGhti0aRNlZWXm8SF/T14zRVxmOplee0YJmvLychYvXoyqqmZ+zdGjR/H5fOZ+TWL1Xysxro2ZLi75tlxGRkYstVyEEHzsYx/jscce469//St1dXUTfqaxsREgI/fcWSsuiZv2VgmLsV8RDAZZuHAhixYtyvmYqci1UyScCTIoKioaY13lu0SLLS75xapz63A44opvhkIhM7/G6NJZWlpKRUWFWZDRinsptgrGTGYyNvSLi4stO96tt97KI488wu9//3uKi4s5ffo0AKWlpXi9Xo4cOcIjjzzCG97wBiorK9m9ezef+tSnuPjiiznnnHPSHuesFJdsc1cmore3l6amJioqKqiqqsq76yAXyyU212bx4sUsXrx4zHkw/p2viDRbXPJLum6xTHG73XHFN/1+vyk2ra2tcZaPUbYkmzmcLZZLNgVsM8Hv91uWewZw7733AtFEyVjuv/9+brzxRlwuF08//TT33HMPPp+PBQsWcO211/KFL3who3HOKnHJNXclFbF97VesWMH8+fPZt29fXnNQIHtxUVWVffv20dPTM26ujXFTT4XlMjw8THd3NxUVFdMmcmmmkS9xiUWSJAoLCyksLDSLbxrJnJ2dnRw8eNAsW2JEomXSGjjf858M8ukWMyprW2m5THS/L1iwYEx2fjacNeJi7IPs3buXFStW4HA48tLX3viR060tlgvZiMvIyAiNjY04nU62bt06bhTQVFku7e3t7Nu3j+LiYo4ePWq2DTb+Z3VgRDrMZAtrMhfn2BpZdXV1aJpmNks7fvw4e/fuNVsDG8EBqRZe47o7GyyXmbihn2/OCnHRdZ1wOIymaXR0dLBs2bK89bU3UBSFSCSS8xjjkam4nDx5kr1797Jw4UKWLl064QVv7ENNluWi6zr79+/n9OnTbNiwwRTqwcFB+vr6zJpKRUVFptDkazP5bGA6CKKiKHFlS4zWwH19fbS0tBAKhcYU34y1mGe6sED+N/SttlwmixktLonthw1rJVeLIrav/erVq6mpqRnznulkuei6bjYgm26Vl40FMBgM0tDQgBDCrF4QDofj/Pf19fWEw2HTv29UBjaS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vfVWZFlW/62++uor2rVrR//+/e257Bqj0YnL+WRnZxMUFMSWLVu4+eab7b2cBoUQgszMTNWTZsuWLXTu3Fn1pLne3pOG7Hd/Nb009hQWq9XKlClTiI+PZ9OmTQ4fkqxLysvLq5Rfz5w5kzfeeIOYmBjmzJlTxUdpxowZfP755yQkJNCiRQt7LLfGafTikpKSQtu2bYmPj6dLly72Xk6DRfGkUYRmw4YNtGvXroonTXWFprH53VfupcnMzMRkMqm9NN7e3hw4cMAuwmKz2fjnP//Jrl271BLaxk5ZWRnff/8969ev58iRI9x4443ceuut3HPPPQDMmjWLTz75hAcffJApU6YQFhbG66+/znvvvceOHTscdnz+tdCoxUWWZUaPHk1BQQHbtm2z93IaDYonzfLly4mNjeW3334jLCxMtQq43GBJIQRJSUlkZWU1Sr97IQRGo1EVmpKSEgwGA61atSI4OLjOemlkWeaJJ55gy5YtbNq0ibCwsDo5riNTVlbG4MGD8fLywmAw0Lp1axYuXAjA3XffzQcffADA+++/z4cffsijjz5Kfn4+n376Kdu3b6dnz572XH6N06jFZerUqaxZs4Zt27bZvSeiMVNUVMSqVauIjY1lzZo1BAUFqaGzyp40VquVQ4cOUVpa2qj97uHvUJirqyu+vr5kZ2dTVFSEj4+PWnlWWx3xsizz7LPPsnbtWjZt2kREREStHKc+YbFY6Ny5M506dWLOnDk0b94cjUbDsWPHeOedd1i7di2TJ0/mnXfeAWDu3Lk88cQTaLVatmzZQp8+fez8CWqeRisujz/+OL/++itbt251XhwORElJCWvWrFE9aXx8fBg9ejTDhw/ngw8+wMPDg2+++cahR4nUNoqweHp60qVLF1V866KXRpZlXnzxRZYtW8amTZto06ZNjfzd+owQgm7duhEREcHy5cvV161WKzqdjlOnTvH0009z6NAhfvjhB2644QYAFixYQIcOHYiKirLX0muVRicuQgj+9a9/sXTpUjZv3kzbtm3tvSQnl0DxpFm0aBELFy5ECME999zD/fffT9++fevVnKWawmw2s2/fPjw8PKoIy8XeV9mXxt3dXS1x9vT0vKZCClmWee2111iwYAGbN292lu//xYcffshLL73Em2++yTPPPAOgjm9Ryozj4+Pp1asXs2fP5p///KedV1w3NDpx+ec//8mCBQv49ddfq1wc3t7ejTrM4qiUlJQwZswYjEYjzzzzDL/99hu//vorkiQxcuRI1ZPG3gMi64LqCsv5WK1WtWkzJycHg8Gg7miq20sjhODtt9/mq6++YuPGjVWGKzZ2Tpw4wQcffEBcXByjR4/mhRdeACrEWJIk9fx26tSJUaNGMWvWrHo5K+xqqb/tn9fI//73PwoLC7nlllsICQlR/1MSb04ci/fffx9Zllm/fj3jxo3jyy+/JD09nZ9++gmDwcAjjzxCq1ateOyxx1i7di0mk8neS64VrlVYAHQ6HU2bNqVbt24MGDCA9u3bY7FYOHDgAFu3buXIkSPk5uYiy/JFf18Iwfvvv6/aADuCsJw9e5b7778ff39/3Nzc6Nq1K3v37q3TNXz11VdkZGQQERHBCy+8QHR0NMuWLePtt98GQKPRqOf02LFjuLm5NZgelurQ6HYuTuoXZrMZm812yV2lzWZj27ZtqlVAcXFxFU+ahrAbvR5huRyyLJOfn6/20siyfEEvjRCCOXPm8N577/H7778THR1dI8e+HvLz84mMjGTgwIFMnTqVwMBAkpOTad26Na1bt66TNSxcuJAXX3yRmJgYnnvuOUJCQkhPT2fWrFns3LmTYcOG8dprr6nv//jjj/n+++9ZsGBBo8lTOcXFSYNBlmV27typCk12djZDhgxhzJgx9dKTBmpPWM5HKQ9XhOa///0vJpMJPz8/fv/9d9atW6cmou3NCy+8wPbt2/njjz/suo63336blStX0qtXL2bMmEHz5s3JzMzk//7v/9i+fTu33347b775JqtWrWL8+PF8//333HnnnXZdc13iFBcnDRJZltm3b5/qSZOWlsbtt9+uetJc74DIuqCuhOV8hBDs2bOHV199le3bt6PVarn99tu58847GT16dJXOcnvQqVMnhgwZQlpaGlu2bKFZs2b885//VH3o65J33nmH5cuXEx0dzfPPP09YWBg5OTnqDsbX15dVq1Yxb948Hn744Tpfnz1xiouTBo8sy8THx7N48WJiY2M5fvw4t912m+pJ4+Pj43BCYy9hgQpx+f7773nuuedYsWIFzZo1Y+nSpcTGxtKpUye+/vrrOlvLxVDK0J9++mnGjRvHnj17mD59Op999hmTJk2qteMuW7aMTp060bRp0ypWAu+99x4LFy6kZ8+ezJgxg1atWpGf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"/>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=3c779b97-b926-4663-a3a8-970cb07175a9">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h2 id="Linear-regression-with-only-one-variable">Linear regression with only one variable<a class="anchor-link" href="#Linear-regression-with-only-one-variable">¶</a></h2><h3 id="Data-separation">Data separation<a class="anchor-link" href="#Data-separation">¶</a></h3>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs" id="cell-id=e2d8381f-562a-46bb-9e0d-08b627ca1260">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [134]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s2">"ENGINESIZE"</span><span class="p">]</span><span class="o">.</span><span class="n">values</span>
<span class="n">y</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s2">"CO2EMISSIONS"</span><span class="p">]</span><span class="o">.</span><span class="n">values</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=6d3975aa-6ffd-4342-ad22-d10018016e52">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [142]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="kn">import</span> <span class="n">train_test_split</span>
<span class="n">xtrain</span><span class="p">,</span> <span class="n">xtest</span><span class="p">,</span> <span class="n">ytrain</span><span class="p">,</span> <span class="n">ytest</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">,</span> <span class="n">test_size</span><span class="o">=</span><span class="mf">0.2</span><span class="p">,</span> <span class="n">random_state</span><span class="o">=</span><span class="mi">4</span><span class="p">)</span>
<span class="n">xtrain</span> <span class="o">=</span> <span class="n">xtrain</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="o">-</span><span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span>
<span class="n">ytrain</span> <span class="o">=</span> <span class="n">ytrain</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="o">-</span><span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span>
<span class="n">xtest</span> <span class="o">=</span> <span class="n">xtest</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="o">-</span><span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span>
<span class="n">ytest</span> <span class="o">=</span> <span class="n">ytest</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="o">-</span><span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">xtest</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">ytest</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">xtrain</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">ytrain</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
<pre>(214, 1) (214, 1)
(853, 1) (853, 1)
</pre>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=1278834c-a449-41d7-a93e-b386e7c73cb3">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [143]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn</span> <span class="kn">import</span> <span class="n">linear_model</span>
<span class="n">regr_</span> <span class="o">=</span> <span class="n">linear_model</span><span class="o">.</span><span class="n">LinearRegression</span><span class="p">()</span>
<span class="n">fregr_</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">xtrain</span><span class="p">,</span><span class="n">ytrain</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[143]:</div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html" tabindex="0">
<style>#sk-container-id-3 {
  /* Definition of color scheme common for light and dark mode */
  --sklearn-color-text: black;
  --sklearn-color-line: gray;
  /* Definition of color scheme for unfitted estimators */
  --sklearn-color-unfitted-level-0: #fff5e6;
  --sklearn-color-unfitted-level-1: #f6e4d2;
  --sklearn-color-unfitted-level-2: #ffe0b3;
  --sklearn-color-unfitted-level-3: chocolate;
  /* Definition of color scheme for fitted estimators */
  --sklearn-color-fitted-level-0: #f0f8ff;
  --sklearn-color-fitted-level-1: #d4ebff;
  --sklearn-color-fitted-level-2: #b3dbfd;
  --sklearn-color-fitted-level-3: cornflowerblue;

  /* Specific color for light theme */
  --sklearn-color-text-on-default-background: var(--sg-text-color, var(--theme-code-foreground, var(--jp-content-font-color1, black)));
  --sklearn-color-background: var(--sg-background-color, var(--theme-background, var(--jp-layout-color0, white)));
  --sklearn-color-border-box: var(--sg-text-color, var(--theme-code-foreground, var(--jp-content-font-color1, black)));
  --sklearn-color-icon: #696969;

  @media (prefers-color-scheme: dark) {
    /* Redefinition of color scheme for dark theme */
    --sklearn-color-text-on-default-background: var(--sg-text-color, var(--theme-code-foreground, var(--jp-content-font-color1, white)));
    --sklearn-color-background: var(--sg-background-color, var(--theme-background, var(--jp-layout-color0, #111)));
    --sklearn-color-border-box: var(--sg-text-color, var(--theme-code-foreground, var(--jp-content-font-color1, white)));
    --sklearn-color-icon: #878787;
  }
}

#sk-container-id-3 {
  color: var(--sklearn-color-text);
}

#sk-container-id-3 pre {
  padding: 0;
}

#sk-container-id-3 input.sk-hidden--visually {
  border: 0;
  clip: rect(1px 1px 1px 1px);
  clip: rect(1px, 1px, 1px, 1px);
  height: 1px;
  margin: -1px;
  overflow: hidden;
  padding: 0;
  position: absolute;
  width: 1px;
}

#sk-container-id-3 div.sk-dashed-wrapped {
  border: 1px dashed var(--sklearn-color-line);
  margin: 0 0.4em 0.5em 0.4em;
  box-sizing: border-box;
  padding-bottom: 0.4em;
  background-color: var(--sklearn-color-background);
}

#sk-container-id-3 div.sk-container {
  /* jupyter's `normalize.less` sets `[hidden] { display: none; }`
     but bootstrap.min.css set `[hidden] { display: none !important; }`
     so we also need the `!important` here to be able to override the
     default hidden behavior on the sphinx rendered scikit-learn.org.
     See: https://github.com/scikit-learn/scikit-learn/issues/21755 */
  display: inline-block !important;
  position: relative;
}

#sk-container-id-3 div.sk-text-repr-fallback {
  display: none;
}

div.sk-parallel-item,
div.sk-serial,
div.sk-item {
  /* draw centered vertical line to link estimators */
  background-image: linear-gradient(var(--sklearn-color-text-on-default-background), var(--sklearn-color-text-on-default-background));
  background-size: 2px 100%;
  background-repeat: no-repeat;
  background-position: center center;
}

/* Parallel-specific style estimator block */

#sk-container-id-3 div.sk-parallel-item::after {
  content: "";
  width: 100%;
  border-bottom: 2px solid var(--sklearn-color-text-on-default-background);
  flex-grow: 1;
}

#sk-container-id-3 div.sk-parallel {
  display: flex;
  align-items: stretch;
  justify-content: center;
  background-color: var(--sklearn-color-background);
  position: relative;
}

#sk-container-id-3 div.sk-parallel-item {
  display: flex;
  flex-direction: column;
}

#sk-container-id-3 div.sk-parallel-item:first-child::after {
  align-self: flex-end;
  width: 50%;
}

#sk-container-id-3 div.sk-parallel-item:last-child::after {
  align-self: flex-start;
  width: 50%;
}

#sk-container-id-3 div.sk-parallel-item:only-child::after {
  width: 0;
}

/* Serial-specific style estimator block */

#sk-container-id-3 div.sk-serial {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: var(--sklearn-color-background);
  padding-right: 1em;
  padding-left: 1em;
}


/* Toggleable style: style used for estimator/Pipeline/ColumnTransformer box that is
clickable and can be expanded/collapsed.
- Pipeline and ColumnTransformer use this feature and define the default style
- Estimators will overwrite some part of the style using the `sk-estimator` class
*/

/* Pipeline and ColumnTransformer style (default) */

#sk-container-id-3 div.sk-toggleable {
  /* Default theme specific background. It is overwritten whether we have a
  specific estimator or a Pipeline/ColumnTransformer */
  background-color: var(--sklearn-color-background);
}

/* Toggleable label */
#sk-container-id-3 label.sk-toggleable__label {
  cursor: pointer;
  display: block;
  width: 100%;
  margin-bottom: 0;
  padding: 0.5em;
  box-sizing: border-box;
  text-align: center;
}

#sk-container-id-3 label.sk-toggleable__label-arrow:before {
  /* Arrow on the left of the label */
  content: "▸";
  float: left;
  margin-right: 0.25em;
  color: var(--sklearn-color-icon);
}

#sk-container-id-3 label.sk-toggleable__label-arrow:hover:before {
  color: var(--sklearn-color-text);
}

/* Toggleable content - dropdown */

#sk-container-id-3 div.sk-toggleable__content {
  max-height: 0;
  max-width: 0;
  overflow: hidden;
  text-align: left;
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-0);
}

#sk-container-id-3 div.sk-toggleable__content.fitted {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-0);
}

#sk-container-id-3 div.sk-toggleable__content pre {
  margin: 0.2em;
  border-radius: 0.25em;
  color: var(--sklearn-color-text);
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-0);
}

#sk-container-id-3 div.sk-toggleable__content.fitted pre {
  /* unfitted */
  background-color: var(--sklearn-color-fitted-level-0);
}

#sk-container-id-3 input.sk-toggleable__control:checked~div.sk-toggleable__content {
  /* Expand drop-down */
  max-height: 200px;
  max-width: 100%;
  overflow: auto;
}

#sk-container-id-3 input.sk-toggleable__control:checked~label.sk-toggleable__label-arrow:before {
  content: "▾";
}

/* Pipeline/ColumnTransformer-specific style */

#sk-container-id-3 div.sk-label input.sk-toggleable__control:checked~label.sk-toggleable__label {
  color: var(--sklearn-color-text);
  background-color: var(--sklearn-color-unfitted-level-2);
}

#sk-container-id-3 div.sk-label.fitted input.sk-toggleable__control:checked~label.sk-toggleable__label {
  background-color: var(--sklearn-color-fitted-level-2);
}

/* Estimator-specific style */

/* Colorize estimator box */
#sk-container-id-3 div.sk-estimator input.sk-toggleable__control:checked~label.sk-toggleable__label {
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-2);
}

#sk-container-id-3 div.sk-estimator.fitted input.sk-toggleable__control:checked~label.sk-toggleable__label {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-2);
}

#sk-container-id-3 div.sk-label label.sk-toggleable__label,
#sk-container-id-3 div.sk-label label {
  /* The background is the default theme color */
  color: var(--sklearn-color-text-on-default-background);
}

/* On hover, darken the color of the background */
#sk-container-id-3 div.sk-label:hover label.sk-toggleable__label {
  color: var(--sklearn-color-text);
  background-color: var(--sklearn-color-unfitted-level-2);
}

/* Label box, darken color on hover, fitted */
#sk-container-id-3 div.sk-label.fitted:hover label.sk-toggleable__label.fitted {
  color: var(--sklearn-color-text);
  background-color: var(--sklearn-color-fitted-level-2);
}

/* Estimator label */

#sk-container-id-3 div.sk-label label {
  font-family: monospace;
  font-weight: bold;
  display: inline-block;
  line-height: 1.2em;
}

#sk-container-id-3 div.sk-label-container {
  text-align: center;
}

/* Estimator-specific */
#sk-container-id-3 div.sk-estimator {
  font-family: monospace;
  border: 1px dotted var(--sklearn-color-border-box);
  border-radius: 0.25em;
  box-sizing: border-box;
  margin-bottom: 0.5em;
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-0);
}

#sk-container-id-3 div.sk-estimator.fitted {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-0);
}

/* on hover */
#sk-container-id-3 div.sk-estimator:hover {
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-2);
}

#sk-container-id-3 div.sk-estimator.fitted:hover {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-2);
}

/* Specification for estimator info (e.g. "i" and "?") */

/* Common style for "i" and "?" */

.sk-estimator-doc-link,
a:link.sk-estimator-doc-link,
a:visited.sk-estimator-doc-link {
  float: right;
  font-size: smaller;
  line-height: 1em;
  font-family: monospace;
  background-color: var(--sklearn-color-background);
  border-radius: 1em;
  height: 1em;
  width: 1em;
  text-decoration: none !important;
  margin-left: 1ex;
  /* unfitted */
  border: var(--sklearn-color-unfitted-level-1) 1pt solid;
  color: var(--sklearn-color-unfitted-level-1);
}

.sk-estimator-doc-link.fitted,
a:link.sk-estimator-doc-link.fitted,
a:visited.sk-estimator-doc-link.fitted {
  /* fitted */
  border: var(--sklearn-color-fitted-level-1) 1pt solid;
  color: var(--sklearn-color-fitted-level-1);
}

/* On hover */
div.sk-estimator:hover .sk-estimator-doc-link:hover,
.sk-estimator-doc-link:hover,
div.sk-label-container:hover .sk-estimator-doc-link:hover,
.sk-estimator-doc-link:hover {
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-3);
  color: var(--sklearn-color-background);
  text-decoration: none;
}

div.sk-estimator.fitted:hover .sk-estimator-doc-link.fitted:hover,
.sk-estimator-doc-link.fitted:hover,
div.sk-label-container:hover .sk-estimator-doc-link.fitted:hover,
.sk-estimator-doc-link.fitted:hover {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-3);
  color: var(--sklearn-color-background);
  text-decoration: none;
}

/* Span, style for the box shown on hovering the info icon */
.sk-estimator-doc-link span {
  display: none;
  z-index: 9999;
  position: relative;
  font-weight: normal;
  right: .2ex;
  padding: .5ex;
  margin: .5ex;
  width: min-content;
  min-width: 20ex;
  max-width: 50ex;
  color: var(--sklearn-color-text);
  box-shadow: 2pt 2pt 4pt #999;
  /* unfitted */
  background: var(--sklearn-color-unfitted-level-0);
  border: .5pt solid var(--sklearn-color-unfitted-level-3);
}

.sk-estimator-doc-link.fitted span {
  /* fitted */
  background: var(--sklearn-color-fitted-level-0);
  border: var(--sklearn-color-fitted-level-3);
}

.sk-estimator-doc-link:hover span {
  display: block;
}

/* "?"-specific style due to the `<a>` HTML tag */

#sk-container-id-3 a.estimator_doc_link {
  float: right;
  font-size: 1rem;
  line-height: 1em;
  font-family: monospace;
  background-color: var(--sklearn-color-background);
  border-radius: 1rem;
  height: 1rem;
  width: 1rem;
  text-decoration: none;
  /* unfitted */
  color: var(--sklearn-color-unfitted-level-1);
  border: var(--sklearn-color-unfitted-level-1) 1pt solid;
}

#sk-container-id-3 a.estimator_doc_link.fitted {
  /* fitted */
  border: var(--sklearn-color-fitted-level-1) 1pt solid;
  color: var(--sklearn-color-fitted-level-1);
}

/* On hover */
#sk-container-id-3 a.estimator_doc_link:hover {
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-3);
  color: var(--sklearn-color-background);
  text-decoration: none;
}

#sk-container-id-3 a.estimator_doc_link.fitted:hover {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-3);
}
</style><div class="sk-top-container" id="sk-container-id-3"><div class="sk-text-repr-fallback"><pre>LinearRegression()</pre><b>In a Jupyter environment, please rerun this cell to show the HTML representation or trust the notebook. <br/>On GitHub, the HTML representation is unable to render, please try loading this page with nbviewer.org.</b></div><div class="sk-container" hidden=""><div class="sk-item"><div class="sk-estimator fitted sk-toggleable"><input checked="" class="sk-toggleable__control sk-hidden--visually" id="sk-estimator-id-3" type="checkbox"/><label class="sk-toggleable__label fitted sk-toggleable__label-arrow fitted" for="sk-estimator-id-3">  LinearRegression<a class="sk-estimator-doc-link fitted" href="https://scikit-learn.org/1.5/modules/generated/sklearn.linear_model.LinearRegression.html" rel="noreferrer" target="_blank">?<span>Documentation for LinearRegression</span></a><span class="sk-estimator-doc-link fitted">i<span>Fitted</span></span></label><div class="sk-toggleable__content fitted"><pre>LinearRegression()</pre></div> </div></div></div></div>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=a0b32468-a6cc-402f-942a-8dbbfecaff16">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<h1 id="Evaluation">Evaluation<a class="anchor-link" href="#Evaluation">¶</a></h1>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=15a66ef0-55ac-40f0-a3f5-44418568b2a3">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [146]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="kn">import</span> <span class="n">r2_score</span>
<span class="n">yhat</span> <span class="o">=</span> <span class="n">regr_</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">xtest</span><span class="p">)</span>
<span class="n">r2_score</span><span class="p">(</span><span class="n">ytest</span><span class="p">,</span> <span class="n">yhat</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[146]:</div>
<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain" tabindex="0">
<pre>0.8149387318398211</pre>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=dcb0ecdd-e002-45d6-927b-46eea1493cb8">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [164]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">ENGINESIZE</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">CO2EMISSIONS</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="s2">"co2"</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s2">"CO2EMISSIONS"</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s2">"ENGINESIZE"</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">xtest</span><span class="p">,(</span><span class="n">regr_</span><span class="o">.</span><span class="n">coef_</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">*</span> <span class="n">xtest</span><span class="p">)</span> <span class="o">+</span> <span class="n">regr_</span><span class="o">.</span><span class="n">intercept_</span> <span class="p">,</span> <span class="s1">'-r'</span><span class="p">,</span><span class="n">label</span><span class="o">=</span><span class="s2">"prediction"</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[164]:</div>
<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain" tabindex="0">
<pre>&lt;matplotlib.legend.Legend at 0x162808fb0&gt;</pre>
</div>
</div>
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedImage jp-OutputArea-output" tabindex="0">
<img alt="No description has been provided for this image" class="" src="data:image/png;base64,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"/>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs" id="cell-id=ea7e3188-fac1-43af-b9c6-b0009358903f">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span> 
</pre></div>
</div>
</div>
</div>
</div>
</div>
</main>
</body>
</html>

 
